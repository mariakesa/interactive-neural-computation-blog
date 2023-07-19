<script>
	import { onMount } from 'svelte';
	import data from '/data/neuropixel_probe_locs.json';

	let chart;

	onMount(async () => {
		const d3 = await import('d3');

		// Set up the SVG container for the scatter plot
		const width = 500;
		const height = 500;

		const svg = d3.select(chart).append('svg').attr('width', width).attr('height', height);

		// Create scales for x and y coordinates
		const xScale = d3
			.scaleLinear()
			.domain([-d3.max(data, (d) => d.x), d3.max(data, (d) => d.x)])
			.range([0, width]);

		const yScale = d3
			.scaleLinear()
			.domain([-d3.max(data, (d) => d.y), d3.max(data, (d) => d.y)])
			.range([height, 0]);

		// Create the scatter plot
		const circles = svg
			.selectAll('circle')
			.data(data)
			.enter()
			.append('circle')
			.attr('cx', (d) => xScale(d.x))
			.attr('cy', (d) => yScale(d.y))
			.attr('r', 3.5)
			.attr('fill', '#34ebb7');

		// Event listener for hover over circles
		circles.on('mouseover', async (event, d) => {
			const imageSrc = `/brainwide-neuropixels-vis/${encodeURIComponent(d.image_filename)}`; // Construct the image URL
			const imageBlob = await fetch(imageSrc).then((response) => response.blob()); // Fetch the image as a Blob
			const imageUrl = URL.createObjectURL(imageBlob); // Create a temporary URL for the image Blob
			updateImage(imageUrl);
		});

		// Set up the SVG container for the image
		const imageWidth = 300; // Set the desired width for the image
		const imageHeight = 200; // Set the desired height for the image

		const imageSvg = d3
			.select(chart)
			.append('svg')
			.attr('width', imageWidth)
			.attr('height', imageHeight);

		// Append the image element
		const imageElement = imageSvg
			.append('image')
			.attr('x', 0)
			.attr('y', 0)
			.attr('width', imageWidth)
			.attr('height', imageHeight);

		// Function to update the image
		const updateImage = (src) => {
			imageElement.attr('xlink:href', src);
		};
	});
</script>

<div bind:this={chart} />

<style>
	/* Your custom styles for the scatter plot and image container can go here */
</style>
