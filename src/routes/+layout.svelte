<nav>
	<a href="/"><strong>Intro Algorithms Svelte App</strong></a>
	<div>
		<a href="/binary-search">Binary Search</a>
	</div>
</nav>

<main>
	<slot />
</main>

<footer style="text-align: center;">
	<hr />
	<p>&copy; 2023 Vadim Gierko</p>
</footer>

<style>
	nav {
		display: flex;
		justify-content: space-between;
		padding: 1em 0;
	}

	main {
		flex-grow: 1;
	}

	a {
		text-decoration: none;
		color: rgb(190, 190, 190);
	}

	a:hover {
		color: rgb(235, 235, 235);
	}
</style>
