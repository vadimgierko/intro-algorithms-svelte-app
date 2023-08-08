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

<h1>Algorithm: Binary Search</h1>

<hr />

<p>
	Binary search is an efficient algorithm for finding an item from a sorted list of items. It works
	by repeatedly dividing in half the portion of the list that could contain the item, until you've
	narrowed down the possible locations to just one.
</p>

<h2>Implementation: Guessing Numbers Game</h2>

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
	h1,
	h2 {
		text-align: center;
	}

	input {
		width: 8em;
		background-color: rgb(59, 59, 59);
		color: rgb(245, 241, 241);
	}

	.guess {
		color: rgb(2, 235, 103);
	}
</style>
