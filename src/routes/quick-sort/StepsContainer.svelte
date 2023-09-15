<script>
	import StepsList from './StepsList.svelte';

	export let steps;
	export let stepsForRandomIndexPivot;
</script>

<div id="container">
	<div>
		<p>Steps for <strong>not random pivot</strong>:</p>
		<StepsList {steps} />
	</div>

	<div>
		<p>Steps for <strong>random pivot</strong>:</p>
		<StepsList steps={stepsForRandomIndexPivot} />
	</div>
</div>

<style>
	#container {
		display: flex;
	}
</style>
