<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<div class="min-h-screen bg-[#F1E8DB]">
	<main>
		{@render children()}
	</main>
</div>
