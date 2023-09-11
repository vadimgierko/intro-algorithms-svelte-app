<script>
	const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

	function insert(array, rightIndex, value) {
		console.log('inserting', value);
		let updatedArray = [...array];

		for (let i = rightIndex; i >= 0; i--) {
			const checkValue = updatedArray[i];

			if (value < checkValue) {
				updatedArray[i] = value;
				updatedArray[i + 1] = checkValue;
			} else {
				console.log(`The element ${value} is on the right place already. No need to insert.`);
				break;
			}
		}

		console.log('updatedArray', updatedArray);
		return updatedArray;
	}

	function sort(array) {
		console.log('sorting...');
		let sortedArray = [...array];

		for (let i = 0; i < sortedArray.length - 1; i++) {
			sortedArray = insert(sortedArray, i, sortedArray[i + 1]);
		}

		return sortedArray;
	}

	const sortedArray = sort(arrayToSort);

	let sortedArrayStepByStep = [...arrayToSort];
	let step = 0;

	function sortStepByStep() {
		if (step >= sortedArrayStepByStep.length - 1) return alert('Array is sorted already!');

		console.log('sorting step by step => step:', step);
		sortedArrayStepByStep = insert(sortedArrayStepByStep, step, sortedArrayStepByStep[step + 1]);
		step = step + 1;
	}

	const code = `
const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

function insert(array, rightIndex, value) {
  console.log("inserting", value)
  let updatedArray = [...array];
  
  for (let i = rightIndex; i >= 0; i--) {
    const checkValue = updatedArray[i];

    if (value < checkValue) {
      updatedArray[i] = value;
      updatedArray[i + 1] = checkValue;
    } else {
      console.log(\`The element \${value} is on the right place already. No need to insert.\`)
      break;
    }
  }

  console.log("updatedArray", updatedArray)
  return updatedArray;
}

function sort(array) {
  console.log("sorting...")
  let sortedArray = [...array];

  for (let i = 0; i < sortedArray.length - 1; i++) {
    sortedArray = insert(sortedArray, i, sortedArray[i + 1])
  }

  return sortedArray;
}

const sortedArray = sort(arrayToSort);
  `;
</script>

<h1>Algorithm: Insertion Sort</h1>

<hr />

<p>
	Loop over positions in the array, starting with index 1. Each new position is like the new card
	handed to you by the dealer, and you need to insert it into the correct place in the sorted
	subarray to the left of that position.
</p>

<h2>Implementation: sorting an array</h2>

<hr />

<p>Array to sort: {arrayToSort}</p>
<p>Sorted array: {sortedArray}</p>

<p>sort step by step:</p>
<p>
	{sortedArrayStepByStep}
	<button on:click={() => sortStepByStep()}>sort step by step ({step})</button>
</p>

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
