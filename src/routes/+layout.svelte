<script>
	import {selectedCard} from '../stores/index'
	import Modal from '../component/Modal.svelte';
	import Sidebar from '../component/Sidebar.svelte';
	import ContentArea from '../component/ContentArea.svelte';
  
	let modalOpen = false;
  </script>
  
  <main>
	<div class="flex">
	  <Sidebar />
  
	  <div class="flex-1 p-4">
		<ContentArea />
	  </div>
	</div>
  </main>
  
  <Modal isOpen={modalOpen} on:close={() => (modalOpen = false)} />
  
  <style>
	/* Add Tailwind CSS classes and custom styles as needed */
  </style>
  