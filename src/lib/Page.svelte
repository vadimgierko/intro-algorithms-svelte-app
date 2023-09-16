<script>
	export let algorithmName = '';
	export let description = [];
	export let implementationTitle = '';
	export let code = '';
</script>

<h1>Algorithm: {algorithmName}</h1>

<hr />

{#each description as paragraph}
	<p>{@html paragraph}</p>
{/each}

<h2>Implementation: {implementationTitle}</h2>

<hr />

<!-- implementation code/app goes here -->
<slot />

<h2>Algorithm code</h2>

<hr />

<pre>
	{code}
</pre>

<style>
	h1,
	h2 {
		text-align: center;
	}

	pre {
		overflow: auto;
	}
</style>
