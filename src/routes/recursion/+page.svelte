<script>
	import Page from '$lib/Page.svelte';
	let inputedNumber = 0;

	function factorial(n) {
		if (n < 0 || n === null || n === undefined) return;

		// base case:
		if (n === 0) {
			return 1;
		}
		// recursive case:
		return n * factorial(n - 1);
	}

	$: result = factorial(inputedNumber);

	const code = `
let inputedNumber = 0;

function factorial(n) {
  if (n < 0 || n === null || n === undefined) return;

  // base case:
  if (n === 0) {
    return 1;
  }
  // recursive case:
  return n * factorial(n - 1);
}

const result = factorial(inputedNumber);
  `;
</script>

<Page
	algorithmName="Recursion"
	{code}
	description={[
		"Recursion has many, many applications. We'll see how to use recursion to compute the factorial function, to determine whether a word is a palindrome, to compute powers of a number, to draw a type of fractal, and to solve the ancient Towers of Hanoi problem. Later modules will use recursion to solve other problems, including sorting."
	]}
	implementationTitle="Factorial"
>
	<p>
		For our first example of recursion, let's look at how to compute the factorial function. We
		indicate the factorial of n by n! For example, 5! equals 1*2*3*4*5.
	</p>

	<label for="number-input">
		Choose number to calculate factorial of it (<span
			><em>not too big number, 21 is considered as big one</em></span
		>)!
	</label>

	<br />

	<input
		name="number-input"
		type="number"
		min={0}
		bind:value={inputedNumber}
		placeholder="choose number to calculate factorial"
	/>

	<p>Factorial of {inputedNumber} = {result}</p>
</Page>

<style>
	input {
		width: 8em;
		background-color: rgb(59, 59, 59);
		color: rgb(245, 241, 241);
	}
</style>
