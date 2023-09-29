<!--https://www.sarasoueidan.com/blog/svg-coordinate-systems/ https://betterprogramming.pub/react-d3-plotting-a-line-chart-with-tooltips-ed41a4c31f4f -->


<script>
    import * as d3 from 'd3';
    import { onMount } from 'svelte';
  
    // Define the vectors
    const vector1 = { x: 30, y: 40 };
    const vector2 = { x: -20, y: -60 };
  
    function createChart() {
      // Create an SVG container
      const svg = d3.select('.chart-container').append('svg')
        .attr('width', 400)
        .attr('height', 400);
  
      // Create the coordinate grid lines
      svg.append('line')
        .attr('x1', 0)
        .attr('y1', 200)
        .attr('x2', 400)
        .attr('y2', 200)
        .attr('stroke', 'gray');
  
      svg.append('line')
        .attr('x1', 200)
        .attr('y1', 0)
        .attr('x2', 200)
        .attr('y2', 400)
        .attr('stroke', 'gray');
  
      // Create vector1
      svg.append('line')
        .attr('x1', 200)
        .attr('y1', 200)
        .attr('x2', 200 + vector1.x)
        .attr('y2', 200 - vector1.y)
        .attr('stroke', 'blue');
  
      // Create vector2
      svg.append('line')
        .attr('x1', 200)
        .attr('y1', 200)
        .attr('x2', 200 + vector2.x)
        .attr('y2', 200 - vector2.y)
        .attr('stroke', 'red');
    }
  
    // Call the chart creation function when the component is mounted
    onMount(createChart);
  </script>
  
  <style>
    /* Add your CSS styles here */
  </style>
  
  <div class="chart-container">
    <!-- Your chart will be rendered here -->
  </div>