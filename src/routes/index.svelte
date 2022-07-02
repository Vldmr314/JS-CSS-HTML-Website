<script lang="ts">
    import Intro from "../lib/main_page/Intro.svelte";
    import About from "../lib/main_page/About.svelte";
    import Portfolio from "../lib/main_page/Portfolio.svelte";
    import Contact from "../lib/main_page/Contact.svelte";
</script>

<svelte:head>
    <title>Vladimir Ryabenko</title>

    <meta name="author" content="Vladimir Ryabenko"/>
    <meta name="description" property="og:title" content="Personal Website of Vladimir Ryabenko"/>
    <meta name="image" property="og:image" content="./img/other/my_photo.jpg"/>
    <meta name="robots" content="all"/>
    <meta name="google" content="notranslate"/>
</svelte:head>

<main>
    <Intro/>
    <About/>
    <Portfolio/>
    <Contact/>
</main>

