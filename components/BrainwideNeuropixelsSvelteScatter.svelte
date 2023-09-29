<script>
	import data from '/data/neuropixel_probe_locs.json';
	//console.log(data);
	import { scaleLinear } from 'd3-scale';
	import { max, min } from 'd3-array';

	let xScale = scaleLinear()
		.domain([min(data, (d) => d.x), max(data, (d) => d.x)]) //Input
		.range([0, 100]); //Output

	let yScale = scaleLinear()
		.domain([min(data, (d) => d.y), max(data, (d) => d.y)]) //Input
		.range([0, 100]);
</script>

<svg>
	{#each data as d}
		<circle cx={xScale(d.x)} cy={yScale(d.y)} r="2" fill="blue" stroke="black" stroke-width="1" />
	{/each}
</svg>
