<!--https://www.sarasoueidan.com/blog/svg-coordinate-systems/ https://betterprogramming.pub/react-d3-plotting-a-line-chart-with-tooltips-ed41a4c31f4f -->


<script>
    import * as d3 from 'd3';
    import { onMount, afterUpdate } from 'svelte';
  
    let data = [10, 20, 30, 40, 50];
    let svg; // Reference to the SVG element
  
    function createChart() {
      // Select the chart container and create an SVG element
      svg = d3.select('.chart-container').append('svg');
  
      // Create and update the chart when data changes
      updateChart();
    }
  
    // Function to update the chart based on the data
    function updateChart() {
      const rects = svg.selectAll('rect').data(data);
  
      // Enter
      rects.enter()
        .append('rect')
        .attr('x', (d, i) => i * 40)
        .attr('y', (d) => 100 - d)
        .attr('width', 30)
        .attr('height', (d) => d);
  
      // Update
      rects
        .attr('x', (d, i) => i * 40)
        .attr('y', (d) => 100 - d)
        .attr('width', 30)
        .attr('height', (d) => d);
  
      // Exit
      rects.exit().remove();
    }
  
    // Call the chart creation function when the component is mounted
    onMount(createChart);
  
    // Update the chart when the data changes
    afterUpdate(updateChart);
  </script>
  
  <style>
    /* Add your CSS styles here */
  </style>
  
  <div class="chart-container">
    <!-- Your chart will be rendered here -->
  </div>
  
