<script lang="ts">
	import Modal from '$lib/components/global/Modal.svelte';
	import Sidebar from '$lib/components/global/Sidebar.svelte';
	import '../app.css';
	let { children } = $props();
</script>

<Sidebar>
	{@render children()}
</Sidebar>

<Modal />
