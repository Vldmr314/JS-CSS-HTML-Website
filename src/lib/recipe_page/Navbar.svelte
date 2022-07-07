<script lang="ts">
	import { base } from '$app/paths';
</script>

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

<style>
	h1 {
		font-family: 'Xirod', sans-serif;
		letter-spacing: 3px;
		font-size: 36px;
		display: flex;
		justify-content: center;
		margin-top: 5vh;
	}

	ul {
		margin: 0;
		list-style: none;
		padding: 25px 0 5px;
		text-align: center;
		text-shadow: 0 0 7px white, 0 0 42px aqua, 0 0 82px aqua, 0 0 92px aqua;
	}

	li {
		display: inline-block;
	}

	li:after {
		content: '|';
		color: aqua;
		display: inline-block;
		vertical-align: top;
	}

	li:last-child:after {
		content: none;
	}

	a {
		text-decoration: none;
		font-family: 'Xirod', sans-serif;
		color: white;
		letter-spacing: 2px;
		position: relative;
		padding-bottom: 5px;
		margin: 0 34px 0 30px;
		font-size: 17px;
		text-transform: uppercase;
		display: inline-block;
		transition: color 0.2s;
	}

	a,
	a:visited {
		color: white;
	}

	a:hover {
		color: aqua;
	}

	a:before,
	a:after {
		content: '';
		position: absolute;
		height: 2px;
		top: auto;
		right: 50%;
		bottom: -5px;
		left: 50%;
		background: aqua;
		transition: 0.8s;
	}

	a:hover:before {
		left: 0;
	}

	a:hover:after {
		right: 0;
	}
</style>
