<script>
	const NUMBERS = Array(100);
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

		const GUESS = Math.floor((min + max) / 2);
		console.log('GUESS:', GUESS);

		guesses = [...guesses, GUESS];

		if (GUESS < inputedNumber) {
			return guessTheNumber(GUESS + 1, max);
		} else if (GUESS > inputedNumber) {
			return guessTheNumber(min, GUESS - 1);
		} else {
			//inputedNumber = null; // <= clear state
			return console.log('Chosen number is:', GUESS);
		}
	}

	$: console.log('inputed number:', inputedNumber);
</script>

<h1>Guessing Numbers - Binary Search</h1>

<hr />

<label for="number-input">Choose the number from 1 to 100 & I will guess it in max. 7 steps!</label>
<br />
<input
	name="number-input"
	type="number"
	min={MIN}
	max={MAX}
	bind:value={inputedNumber}
	placeholder="choose number"
/>

<button
	on:click={() => {
		guesses = []; // <= clear state
		guessTheNumber();
	}}>guess</button
>

<p>Guesses:</p>
<ol>
	{#each guesses as guess, i}
		<li key={'guess-' + i} class={i === guesses.length - 1 ? 'guess' : ''}>{guess}</li>
	{/each}
</ol>

<style>
	input {
		width: 8em;
		background-color: rgb(59, 59, 59);
		color: rgb(245, 241, 241);
	}

	ol {
		margin: auto;
		max-width: 360px;
		text-align: start;
	}

	.guess {
		background-color: rgb(0, 118, 0);
	}
</style>
