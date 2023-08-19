<script>
	import data from '/data/neuropixel_probe_locs.json';
	console.log(data);
	import { scaleLinear } from 'd3-scale';
	import * as d3 from 'd3';

	let xScale = scaleLinear()
		.domain([d3.min(data, (d) => d.x), d3.max(data, (d) => d.x)]) //Input
		.range([0, 100]); //Output

	let yScale = scaleLinear()
		.domain([d3.min(data, (d) => d.y), d3.max(data, (d) => d.y)]) //Input
		.range([0, 100]);
</script>

<svg>
	{#each data as d}
		<circle cx={xScale(d.x)} cy={yScale(d.y)} r="2" fill="blue" stroke="black" stroke-width="1" />
	{/each}
</svg>
