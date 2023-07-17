<script>
  import { onMount } from 'svelte';
  import { selectedCard } from '../stores'; // Svelte store to track the selected card

  onMount(() => {
    selectedCard.set(null); // Initialize the selected card to null
  });
</script>

<h1 class="text-2xl font-semibold mb-4">Page 1</h1>

<!-- Add your page 1 content here -->
