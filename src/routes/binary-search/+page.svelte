<script>
	import Page from '$lib/Page.svelte';

	const MIN = 1;
	const MAX = 100;

	let inputedNumber = null;
	let guesses = [];

	function guessTheNumber(min = MIN, max = MAX) {
		if (!inputedNumber) return alert("You didn't provide the number. Cannot guess the number...");

		if (inputedNumber < 1 || inputedNumber > 100)
			return alert(
				'Provided number is invalid. Valid numbers are in the range 1-100. Cannot guess the number...'
			);

		console.log('min:', min);
		console.log('max:', max);

		// divide in half the portion of the list:
		const GUESS = Math.floor((min + max) / 2);
		console.log('GUESS:', GUESS);

		// we collect all guesses to list them:
		guesses = [...guesses, GUESS];

		// if GUESS is smaller or greater then the number we search for
		// we use recursion and continue searching,
		// if GUESS is correct, we stop execution of the function
		// (the guessed number is the last in guesses array):
		if (GUESS < inputedNumber) {
			return guessTheNumber(GUESS + 1, max);
		} else if (GUESS > inputedNumber) {
			return guessTheNumber(min, GUESS - 1);
		} else {
			return console.log('Chosen number is:', GUESS);
		}
	}

	// when inputed number changes, clear the guesses state:
	$: {
		console.log('inputed number:', inputedNumber);
		guesses = [];
	}

	const code = `
const MIN = 1;
const MAX = 100;

let inputedNumber = null; // this is set on input value change
let guesses = []; // we collect all guesses to list them for user

function guessTheNumber(min = MIN, max = MAX) {
	if (!inputedNumber) return alert("You didn't provide the number. Cannot guess the number...");

	if (inputedNumber < 1 || inputedNumber > 100)
		return alert(
			'Provided number is invalid. Valid numbers are in the range 1-100. Cannot guess the number...'
		);
	
	// divide in half the portion of the list:
	const GUESS = Math.floor((min + max) / 2);

	// we collect all guesses to list them for user:
	guesses = [...guesses, GUESS];

	// if GUESS is smaller or greater then the number we search for
	// we use recursion and continue searching,
	// if GUESS is correct, we stop execution of the function
	// (the guessed number is the last in guesses array):
	
	if (GUESS < inputedNumber) {
		return guessTheNumber(GUESS + 1, max);
	} else if (GUESS > inputedNumber) {
		return guessTheNumber(min, GUESS - 1);
	} else {
		return console.log('Chosen number is:', GUESS);
	}
}
	`;
</script>

<Page
	algorithmName="Binary Search"
	{code}
	description={[
		`Binary search is an efficient algorithm for <strong>finding an item from a sorted list of items</strong>. It works by repeatedly <strong>dividing in half the portion of the list</strong> that could contain the item, until you've narrowed down the possible locations to just one.`,
		`	Binary search is more efficient than js method <code>.find()</code>, because <code>.find()</code> will iterate on every element of an array, which is not efficient on large sets.`
	]}
	implementationTitle="Guessing Numbers Game"
>
	<label for="number-input"
		>Choose the number from 1 to 100 & I will guess it in max. 7 steps!</label
	>
	<br />
	<input
		name="number-input"
		type="number"
		min={MIN}
		max={MAX}
		bind:value={inputedNumber}
		placeholder="choose number"
	/>

	<button on:click={() => guessTheNumber()}>guess</button>

	{#if guesses.length}
		<p>Guesses:</p>
		<ol>
			{#each guesses as guess, i}
				<li key={'guess-' + i} class={i === guesses.length - 1 ? 'guess' : ''}>{guess}</li>
			{/each}
		</ol>
	{/if}
</Page>

<style>
	input {
		width: 8em;
		background-color: rgb(59, 59, 59);
		color: rgb(245, 241, 241);
	}

	.guess {
		color: rgb(2, 235, 103);
	}
</style>
