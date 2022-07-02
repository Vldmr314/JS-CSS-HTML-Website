<script lang="ts">
    import {base} from '$app/paths';

    let path = base + "/img/backgrounds/portf_back.gif"
</script>

<div class="portfolio" id="portfolio" style="--image: url({path});">
    <h1>My Portfolio</h1>

    <p>Hope I will add something here soon:)</p>
</div>

<style>
    .portfolio {
        margin: 0;
        position: absolute;
        top: 200vh;
        height: 100vh;
        width: 100vw;
        background-image: var(--image);
        background-size: cover;
        color: white;
    }

    h1 {
        font-family: "Xirod", sans-serif;
        letter-spacing: 3px;
        font-size: 46px;
        display: flex;
        justify-content: center;
        margin-top: 5vh;
    }

    p {
        color: white;
        font-family: "Xirod", sans-serif;
        letter-spacing: 4px;
        font-size: 22px;
        display: flex;
        justify-content: center;
    }
</style>