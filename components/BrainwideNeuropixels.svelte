<script>
	import { onMount } from 'svelte';
	import data from '/data/neuropixel_probe_locs.json';

	let chart;

	onMount(async () => {
		const d3 = await import('d3');

		// Load the JSON data;
		//const response = await fetch('/public/neuropixel_probe_locs.json');

		//const data = await response.json();

		// Set up the SVG container
		const width = 800;
		const height = 800;

		const svg = d3.select(chart).append('svg').attr('width', width).attr('height', height);

		// Create scales for x and y coordinates
		const xScale = d3
			.scaleLinear()
			.domain([0, d3.max(data, (d) => d.x)])
			.range([0, width]);

		const yScale = d3
			.scaleLinear()
			.domain([0, d3.max(data, (d) => d.y)])
			.range([height, 0]);

		// Create the scatter plot
		svg
			.selectAll('circle')
			.data(data)
			.enter()
			.append('circle')
			.attr('cx', (d) => xScale(d.x))
			.attr('cy', (d) => yScale(d.y))
			.attr('r', 5)
			.attr('fill', 'steelblue');
	});
</script>

<div bind:this={chart} />
