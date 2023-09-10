<script>
	const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

	function swap(array, firstIndex, secondIndex) {
		const temp = array[firstIndex];
		array[firstIndex] = array[secondIndex];
		array[secondIndex] = temp;

		return array;
	}

	function indexOfMinimum(array, startIndex) {
		let minValue = array[startIndex];
		let minIndex = startIndex;

		for (let i = minIndex + 1; i < array.length; i++) {
			if (array[i] < minValue) {
				minIndex = i;
				minValue = array[i];
			}
		}

		return minIndex;
	}

	function selectionSort(array) {
		let sortedArray = [...array];

		for (let i = 0; i < sortedArray.length; i++) {
			const minIndex = indexOfMinimum(sortedArray, i);
			sortedArray = swap(sortedArray, i, minIndex);
		}

		return sortedArray;
	}

	const sortedArray = selectionSort(arrayToSort);

	//================ VISUALIZATION STEP BY STEP ================//
	let step = 0;
	let visualized = [...arrayToSort];

	function sortStepByStep(array, index) {
		if (index > array.length - 1) return alert('Array is sorted already!');

		const minIndex = indexOfMinimum(array, index);
		visualized = swap(array, index, minIndex);
		step++;
	}

	function clearVisualization() {
		step = 0;
		visualized = [...arrayToSort];
	}

	//============================================================//

	const code = `
const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

function swap(array, firstIndex, secondIndex) {
  const temp = array[firstIndex];
  array[firstIndex] = array[secondIndex];
  array[secondIndex] = temp;

  return array;
}

function indexOfMinimum(array, startIndex) {
  let minValue = array[startIndex];
  let minIndex = startIndex;

  for (let i = minIndex + 1; i < array.length; i++) {
    if (array[i] < minValue) {
      minIndex = i;
      minValue = array[i];
    }
  }

  return minIndex;
}

function selectionSort(array) {
  let sortedArray = [...array];

  for (let i = 0; i < sortedArray.length; i++) {
    const minIndex = indexOfMinimum(sortedArray, i);
    sortedArray = swap(sortedArray, i, minIndex);
  }

  return sortedArray;
}

const sortedArray = selectionSort(arrayToSort);
  `;
</script>

<h1>Algorithm: Selection Sort</h1>

<hr />

<p>
	This algorithm is called selection sort because it repeatedly selects the next-smallest element
	and swaps it into place. As selection sort runs, the subarray at the beginning of the array is
	sorted, but the subarray at the end is not. Selection sort scans the unsorted subarray for the
	next element to include in the sorted subarray. In selection sort, each element that you add to
	the sorted subarray is no smaller than the elements already in the sorted subarray.
</p>

<h2>Implementation: sorting an array</h2>

<hr />

<p>Array to sort: {arrayToSort}</p>
<p>Sorted array: {sortedArray}</p>

<h2>Selection sort visualizer</h2>

<p>Click next button to sort array step by step!</p>
<p>
	{visualized}
	<button on:click={() => sortStepByStep(visualized, step)}>sort step by step</button>
	<button on:click={clearVisualization}>restart</button>
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
