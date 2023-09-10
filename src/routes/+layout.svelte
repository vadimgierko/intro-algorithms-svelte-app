<nav>
	<a href="/"><strong>Intro To Algorithms</strong></a>
	<div>
		<a href="/binary-search">binary search</a> |
		<a href="/recursion">recursion</a> |
		<a href="/selection-sort">selection sort</a>
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
