<script lang="ts" context="module">
    import { base } from '$app/paths';
    export const prerender = false;
</script>

<script lang="ts">
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

<div class="recipe" id="recipe">
    <header>
        <nav>
            <ul>
                <li><a href="{base}/">Main Page</a></li>
                <li><a href="{base}/#about">About Me</a></li>
                <li><a href="{base}/#portfolio">Portfolio</a></li>
                <li><a href="{base}/#contact">My Contacts</a></li>
            </ul>
        </nav>

        <h1>Random Cocktail Recipe</h1>
    </header>
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
            <img alt="drink" src={drinkPhoto || base+"/img/other/defolt_cocktail.jpg"} height="400"/>
        </div>
    </div>

    <div class="button-wrapper">
        <button on:click={handleClick}><span>Get recipe!</span></button>
    </div>
</div>

<style>
    @font-face {
        font-family: "Xirod";
        src: url("PersonalWebsite/fonts/xirod.woff2") format("woff2"),
        url("PersonalWebsite/fonts/xirod.woff") format("woff");
        font-weight: normal;
        font-style: normal;
        font-display: swap;
    }

    :global(body) {
        padding: 0;
        margin: 0;
        overflow-x: hidden;
        text-shadow: 0 0 7px white,
        0 0 42px aqua,
        0 0 82px aqua;
    }

    .recipe {
        margin: 0;
        position: absolute;
        height: 100vh;
        width: 100vw;
        background: url("PersonalWebsite/img/other/recipe.jpg") no-repeat;
        background-size: cover;
        color: white;
    }

    h1 {
        font-family: "Xirod", sans-serif;
        letter-spacing: 3px;
        font-size: 36px;
        display: flex;
        justify-content: center;
        margin-top: 5vh;
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

    ul {
        margin: 0;
        list-style: none;
        padding: 25px 0 5px;
        text-align: center;
        text-shadow: 0 0 7px white,
        0 0 42px aqua,
        0 0 82px aqua,
        0 0 92px aqua;
    }

    li {
        display: inline-block;
    }

    li:after {
        content: "|";
        color: aqua;
        display: inline-block;
        vertical-align: top;
    }

    li:last-child:after {
        content: none;
    }

    a {
        text-decoration: none;
        font-family: "Xirod", sans-serif;
        color: white;
        letter-spacing: 2px;
        position: relative;
        padding-bottom: 5px;
        margin: 0 34px 0 30px;
        font-size: 17px;
        text-transform: uppercase;
        display: inline-block;
        transition: color .2s;
    }

    a, a:visited {
        color: white;
    }

    a:hover {
        color: aqua;
    }

    a:before,
    a:after {
        content: "";
        position: absolute;
        height: 2px;
        top: auto;
        right: 50%;
        bottom: -5px;
        left: 50%;
        background: aqua;
        transition: .8s;
    }

    a:hover:before {
        left: 0;
    }

    a:hover:after {
        right: 0;
    }
</style>
