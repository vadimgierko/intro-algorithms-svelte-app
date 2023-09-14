<script>
	const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

	const steps = []; // for displaying sort steps

	function quickSort(array) {
		console.log('quick sorting...');

		const pivot = array[0];
		let leftArray = [];
		let rightArray = [];

		if (array.length <= 1) return array;

		for (let i = 1; i < array.length; i++) {
			const element = array[i];
			console.log({ element });
			if (element < pivot) {
				leftArray.push(element);
			} else if (element > pivot) {
				rightArray.push(element);
			}
		}

		steps.push({ array, left: leftArray, pivot, right: rightArray });

		return [...quickSort(leftArray), pivot, ...quickSort(rightArray)];
	}

	const sortedArray = quickSort(arrayToSort);

	//============================ CODE ===================================//

	const code = `
const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

function quickSort(array) {
	const pivot = array[0];
	let leftArray = [];
	let rightArray = [];

	if (array.length <= 1) return array;
	
	for (let i = 1; i < array.length; i++) {
		const element = array[i];
	
		if (element < pivot) {
			leftArray.push(element)
		} else if (element > pivot) {
			rightArray.push(element)
		}
	}

	return [...quickSort(leftArray), pivot, ...quickSort(rightArray)]
}

const sortedArray = quickSort(arrayToSort);
 `;
</script>

<h1>Algorithm: Quick Sort</h1>

<hr />

<p>
	Quick sort is a divide-and-conquer algorithm that sorts an array by choosing a pivot element and
	partitioning the array into two subarrays, one containing elements smaller than the pivot, and the
	other containing elements larger than the pivot. The two subarrays are then recursively sorted
	until the entire array is sorted. The pivot is usually selected as the first or last element of
	the array.
</p>

<h2>Implementation of the quick sort algorithm</h2>

<hr />

<p>Array to sort: {arrayToSort}</p>
<p>Sorted array: {sortedArray}</p>

<p>Steps:</p>
<ol>
	{#each steps as { array, left, pivot, right }}
		<li>
			array: {array};
			<br />
			left: {left}, pivot: {pivot}, right: {right}
		</li>
	{/each}
</ol>

<h2>Algorithm Code</h2>

<hr />

<pre>{code}</pre>

<style>
	h1,
	h2 {
		text-align: center;
	}

	pre {
		overflow: auto;
	}
</style>
