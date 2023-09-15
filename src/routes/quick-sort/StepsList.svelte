<script>
	export let steps = [];
</script>

<ol>
	{#each steps as { array, left, pivot, right }}
		<li>
			array: {array};
			<br />
			left: {#if left.length === 1}<span class="inplace">{left}</span>{:else}{left}{/if}, pivot:
			<span class="inplace">{pivot}</span>, right: {#if right.length === 1}<span class="inplace"
					>{right}</span
				>{:else}{right}{/if}
		</li>
	{/each}
</ol>

<style>
	.inplace {
		background-color: green;
	}
</style>
