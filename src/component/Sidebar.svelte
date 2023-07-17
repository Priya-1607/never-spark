<script>
  import { onMount } from 'svelte';
 import {data1} from "./data"
  import { selectedCard } from '../stores'; // Svelte store to track the selected card

  let searchQuery = '';
  let filteredData = [];
  let isDrawerOpen = true; // Initialize the sidebar as open

  function filterData() {
    filteredData = data1.filter((item) =>
      item.title.toLowerCase().includes(searchQuery.toLowerCase())
    );
  }

  onMount(filterData);

  function toggleDrawer() {
    isDrawerOpen = !isDrawerOpen;
  }

  function selectCard(card) {
    selectedCard.set(card);
  }
</script>

<div class="flex flex-col h-full w-64 border-r border-gray-200">
  <div class="p-4 flex justify-between items-center">
    <h2 class="text-lg font-semibold">Sidebar</h2>
    <button
      type="button"
      class="p-1 rounded-md hover:bg-gray-200"
      on:click={toggleDrawer}
    >
      {isDrawerOpen ? 'Collapse' : 'Expand'}
    </button>
  </div>

  {#if isDrawerOpen}
    <div class="p-4 border-b border-gray-200">
      <input
        type="text"
        placeholder="Search"
        bind:value={searchQuery}
        on:input={filterData}
        class="p-2 border-b border-gray-200"
      />
    </div>

    {#if filteredData.length === 0}
      <p class="p-4 text-center text-gray-500">No results found.</p>
    {:else}
      {#each filteredData as item (item.id)}
        <div
          class="p-4 border-b border-gray-200 cursor-pointer"
          on:click={() => selectCard(item)}
        >
          <h3 class="text-lg font-semibold">{item.title}</h3>
          <p>{item.description}</p>
        </div>
      {/each}
    {/if}
  {/if}
</div>
