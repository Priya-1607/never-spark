<script>
    import { onMount } from 'svelte';
    import { selectedCard } from '../stores'; // Svelte store to track the selected card
    import { data2 } from './data'; // Dummy data for content area cards
  
    let searchQuery = '';
    let filteredData = [];
  
    function filterData() {
      filteredData = data2.filter((item) =>
        item.title.toLowerCase().includes(searchQuery.toLowerCase())
      );
    }
  
    onMount(filterData);
  
    let expanded = false;
  
    function toggleExpanded() {
      expanded = !expanded;
    }
  
    // Subscribe to changes in the selected card
    let selected;
    selectedCard.subscribe((value) => {
      selected = value;
    });
  </script>
  
  <div class="flex flex-col w-full">
    {#if selected}
      <button
        on:click={toggleExpanded}
        class="px-4 py-2 text-sm font-medium text-gray-500"
      >
        {expanded ? 'Collapse' : 'Expand'}
      </button>
  
      {#if expanded}
        {#each filteredData as item (item.id)}
          <div class="p-4 border-b border-gray-200">
            <h3 class="text-lg font-semibold">{item.title}</h3>
            <p>{item.description}</p>
          </div>
        {/each}
      {/if}
    {/if}
  </div>
  