<script>
    import { onMount } from 'svelte';
    import { data2 } from './data'; // Dummy data for content area cards
  
    let searchQuery = '';
    let filteredData = [];
  
    function filterData() {
      filteredData = data2.filter((item) =>
        item.title.toLowerCase().includes(searchQuery.toLowerCase())
      );
    }
  
    onMount(filterData);
  </script>
  
  <h1 class="text-2xl font-semibold mb-4">Page 2</h1>
  
  <!-- Add your page 2 content here -->
  