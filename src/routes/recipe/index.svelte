<script lang="ts" context="module">
    import {base} from '$app/paths';

    let path = base + "/img/other/recipe.jpg";
    let drink_path = base + "/img/other/defolt_cocktail.jpg"

    export const prerender = false;
</script>

<script lang="ts">
    import Navbar from "../../lib/recipe_page/Navbar.svelte";

    let drinkName: string;
    let instructions: string;
    let ingredients: string;
    let drinkPhoto: HTMLImageElement;

    interface RecipeJson {
        elements: Record<string, Array<Record<string, any>>>;
    }

    interface Recipe {
        drinkName: string;
        instructions: string;
        ingredients: string;
        drinkPhoto: HTMLImageElement;
    }

    async function fetchSomeRecipe(): Promise<RecipeJson> {
        return {elements: await fetch("https://www.thecocktaildb.com/api/json/v1/1/random.php").then(r => r.json())};
    }

    function parseRecipe(recipeJson: RecipeJson): Recipe {
        const drinks = recipeJson.elements.drinks;
        const {
            strDrink, strInstructions, strDrinkThumb, strIngredient1, strIngredient2, strIngredient3, strIngredient4,
            strIngredient5, strIngredient6, strIngredient7, strIngredient8
        } = drinks[0];
        const ingredient_list: Array<string | null> = [strIngredient1, strIngredient2, strIngredient3, strIngredient4,
            strIngredient5, strIngredient6, strIngredient7, strIngredient8];

        let strIngredients = "";
        for (let i = 0; i < 8; i++) {
            if (ingredient_list[i] != null) {
                strIngredients += ingredient_list[i] + ", ";
            }
        }
        strIngredients = strIngredients.slice(0, -2);

        return {
            drinkName: strDrink,
            ingredients: strIngredients,
            instructions: strInstructions,
            drinkPhoto: strDrinkThumb
        };
    }

    function setParams(recipe: Recipe) {
        ingredients = recipe.ingredients;
        drinkName = recipe.drinkName;
        instructions = recipe.instructions;
        drinkPhoto = recipe.drinkPhoto;
    }

    async function handleClick() {
        drinkName = instructions = "Loading...";
        const recipeJson: RecipeJson = await fetchSomeRecipe();
        const recipe: Recipe = parseRecipe(recipeJson);
        setParams(recipe);
    }

</script>

<div class="recipe" id="recipe" style="--image: url({path});">
    <Navbar />

    <h2>{drinkName || "Balmoral"}</h2>

    <div class="recipe-wrapper">
        <div class="recipe-info">
            <div class="recipe-text">
                <p>Ingredients: </p>
                <p>{ingredients || "Scotch, Sweet Vermouth, Dry Vermouth, Bitters"}</p>
                <p>Instruction: </p>
                <p>{instructions || "In a mixing glass half-filled with ice cubes, combine all of the ingredients." +
                " Stir well. Strain into a cocktail glass."}</p>
            </div>
            <img alt="drink"
                 src={drinkPhoto || drink_path}
                 height="400"/>
        </div>
    </div>

    <div class="button-wrapper">
        <button on:click={handleClick}><span>Get recipe!</span></button>
    </div>
</div>

<style>
    .recipe {
        margin: 0;
        position: absolute;
        height: 100vh;
        width: 100vw;
        background-image: var(--image);
        background-size: cover;
        color: white;
    }

    h2 {
        font-family: "Xirod", sans-serif;
        letter-spacing: 3px;
        font-size: 22px;
        display: flex;
        justify-content: center;
        margin-top: 5vh;
    }

    .recipe-wrapper {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        margin-top: 5vh;
    }

    .recipe-info {
        display: flex;
        justify-content: space-between;
        width: 70%;
    }

    img {
        box-shadow: 0 0 7px white,
        0 0 42px aqua;
    }

    .recipe-text {
        width: 60%;
    }

    p {
        font-family: "Xirod", sans-serif;
        letter-spacing: 2px;
        font-size: 18px;
    }

    .button-wrapper {
        display: flex;
        justify-content: center;
        margin-top: 3vh;
    }

    button {
        background-image: linear-gradient(to right, #006175 0%, #00a950 100%);
        border-radius: 40px;
        box-sizing: border-box;
        color: #00a84f;
        display: block;
        height: 50px;
        font-size: 1.4em;
        padding: 4px;
        position: relative;
        text-decoration: none;
        width: 7em;
        z-index: 2;
    }

    button:hover {
        color: #fff;
    }

    span {
        align-items: center;
        background: #0e0e10;
        border-radius: 40px;
        display: flex;
        justify-content: center;
        height: 100%;
        transition: background 0.5s ease;
        width: 100%;
    }

    button:hover span {
        background: transparent;
    }
</style>
