<script lang="ts">
	import Intro from '../lib/main_page/Intro.svelte';
	import About from '../lib/main_page/About.svelte';
	import Portfolio from '../lib/main_page/Portfolio.svelte';
	import Contact from '../lib/main_page/Contact.svelte';
</script>

<svelte:head>
	<title>Vladimir Ryabenko</title>

	<meta name="author" content="Vladimir Ryabenko" />
	<meta name="description" property="og:title" content="Personal Website of Vladimir Ryabenko" />
	<meta name="image" property="og:image" content="./img/other/my_photo.jpg" />
	<meta name="robots" content="all" />
	<meta name="google" content="notranslate" />
</svelte:head>

<main>
	<Intro />
	<About />
	<Portfolio />
	<Contact />
</main>

<style>
	@font-face {
		font-family: 'Xirod';
		src: url('/PersonalWebsite/fonts/xirod.woff2') format('woff2'),
			url('/PersonalWebsite/fonts/xirod.woff') format('woff');
		font-weight: normal;
		font-style: normal;
		font-display: swap;
	}

	:global(body) {
		padding: 0;
		margin: 0;
		overflow-x: hidden;
		text-shadow: 0 0 7px white, 0 0 42px aqua, 0 0 82px aqua;
	}
</style>
