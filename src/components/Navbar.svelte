<script lang="ts">
	import { onMount } from 'svelte';

	export let currentPage: string = 'home';
	let showQuokkaSecret = false;

	onMount(() => {
		const quokkaSecret = localStorage.getItem('quokkaSecret');
		if (quokkaSecret === 'true') {
			showQuokkaSecret = true;
		}
	});
</script>

<nav class="flex items-center justify-between md:px-24 px-4">
	<div class="text-xl font-semibold">Quokka Corner</div>
	<div class="flex items-center gap-4">
		{#if currentPage === 'status' || currentPage === 'quokka'}
			<a href="/" class="uppercase transition duration-300 ease-in-out hover:opacity-70">Home</a>
		{/if}
		{#if currentPage === 'home' || currentPage === 'quokka'}
			<a href="/status" class="uppercase transition duration-300 ease-in-out hover:opacity-70"
				>Status</a
			>
		{/if}
		{#if showQuokkaSecret && currentPage !== 'quokka'}
			<a href="/quokka" class="uppercase transition duration-300 ease-in-out hover:opacity-70"
				>Quokka</a
			>
		{/if}
	</div>
</nav>
