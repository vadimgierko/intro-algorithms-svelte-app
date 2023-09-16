<script>
	import Page from '$lib/Page.svelte';
	import StepsContainer from './StepsContainer.svelte';

	const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

	// for displaying sort steps list:
	const steps = [];
	const stepsForRandomIndexPivot = [];

	function quickSort({ array = [], randomPivot = true }) {
		// if we use random index for pivot,
		// it may make the algorithm more efficient in case of iterations/complexity:
		const index = randomPivot ? Math.floor(Math.random() * array.length) : 0;
		const pivot = array[index];

		let leftArray = [];
		let rightArray = [];

		if (array.length <= 1) return array;

		for (let i = 1; i < array.length; i++) {
			const element = array[i];

			if (element < pivot) {
				leftArray.push(element);
			} else if (element > pivot) {
				rightArray.push(element);
			}
		}

		if (randomPivot) {
			stepsForRandomIndexPivot.push({ array, left: leftArray, pivot, right: rightArray });
		} else {
			steps.push({ array, left: leftArray, pivot, right: rightArray });
		}

		console.log(leftArray, pivot, rightArray);

		return [
			...quickSort({ array: leftArray, randomPivot }),
			pivot,
			...quickSort({ array: rightArray, randomPivot })
		];
	}

	const sortedArray = quickSort({ array: arrayToSort, randomPivot: false });
	const sortedArrayWithRandomPivot = quickSort({ array: arrayToSort }); // this needed to populate steps

	//============================ CODE ===================================//

	const code = `
const arrayToSort = [22, 11, 66, 99, 88, 9, 7, 42];

function quickSort(array) {
	// if we use random index for pivot,
	// it may make the algorithm more efficient in case of iterations/complexity:
	const index = Math.floor(Math.random() * array.length); // usually pivot is the first element, so index = 0;
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
 `;
</script>

<Page
	algorithmName="Quick Sort"
	{code}
	description={[
		'Quick sort is a divide-and-conquer algorithm that sorts an array by choosing a pivot element and partitioning the array into two subarrays, one containing elements smaller than the pivot, and the other containing elements larger than the pivot. The two subarrays are then recursively sorted until the entire array is sorted.',
		`The <strong>pivot</strong> is usually selected as the <strong>first or last element</strong> of the array, but if we use <u><strong>random index</strong></u> for pivot, it may make the algorithm more efficient in case of iterations/ complexity.`
	]}
	implementationTitle="sorting an array"
>
	<p>Array to sort: {arrayToSort}</p>
	<p>Sorted array: {sortedArray}</p>

	<StepsContainer {steps} {stepsForRandomIndexPivot} />
</Page>
