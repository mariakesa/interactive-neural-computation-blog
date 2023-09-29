<!--https://www.sarasoueidan.com/blog/svg-coordinate-systems/ https://betterprogramming.pub/react-d3-plotting-a-line-chart-with-tooltips-ed41a4c31f4f -->

<script>

    import * as d3 from 'd3';

    const margin = { top: 50, right: 50, bottom: 50, left: 50 };

    const width=100;
    const height=200;

    //const yMinValue = d3.min(data, d => d.value);
    //const yMaxValue = d3.max(data, d => d.value);
    //const xMinValue = d3.min(data, d => d.label);
    //const xMaxValue = d3.max(data, d => d.label);

    const svg = d3
        .select('#container')
        .append('svg')
        .attr('width', width + margin.left + margin.right)
        .attr('height', height + margin.top + margin.bottom)
        .append('g')
        .attr('transform', `translate(${margin.left},${margin.top})`);

</script>

<p>hello</p>