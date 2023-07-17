<script>
  import { createEventDispatcher } from 'svelte';

  export let isOpen = false;

  const dispatch = createEventDispatcher();

  let newCard = {
    title: '',
    description: ''
  };

  function closeModal() {
    dispatch('close');
  }

  function handleTitleInput(event) {
    newCard.title = event.target.value;
  }

  function handleDescriptionInput(event) {
    newCard.description = event.target.value;
  }

  function addNewCard() {
    // Dispatch an event to pass the new card data to the parent component
    dispatch('add', newCard);

    // Reset the newCard object for future additions
    newCard = {
      title: '',
      description: ''
    };
  }
</script>

<div
  class="fixed inset-0 flex items-center justify-center z-50 bg-black bg-opacity-50"
  style="display: {isOpen ? 'flex' : 'none'}"
>
  <div class="bg-white p-4">
    <h2 class="text-xl font-semibold mb-4">Add New Card</h2>

    <form>
      <div class="mb-4">
        <label class="block mb-2 font-medium" for="title">Title</label>
        <input type="text" id="title" bind:value={newCard.title} on:input={handleTitleInput} class="p-2 border border-gray-300 rounded w-full" />
      </div>

      <div class="mb-4">
        <label class="block mb-2 font-medium" for="description">Description</label>
        <textarea id="description" bind:value={newCard.description} on:input={handleDescriptionInput} class="p-2 border border-gray-300 rounded w-full" rows="4"></textarea>
      </div>

      <div class="flex justify-end">
        <button type="button" class="px-4 py-2 bg-gray-200 text-gray-800 rounded-lg mr-2" on:click={closeModal}>Close</button>
        <button type="button" class="px-4 py-2 bg-blue-500 text-white rounded-lg" on:click={addNewCard}>Add Card</button>
      </div>
    </form>
  </div>
</div>
