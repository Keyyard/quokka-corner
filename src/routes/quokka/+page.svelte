<script lang="ts">
	import Banner from '../../components/Banner.svelte';
	import Navbar from '../../components/Navbar.svelte';
	import { onMount } from 'svelte';
	import QuokkaIllustration from '../../components/QuokkaIllustration.svelte';

	let happiness = 100;
	let hunger = 100;
	let energy = 100;
	let lastInteraction = Date.now();
	let isSleeping = false;
	let currentMood: 'happy' | 'content' | 'sad' | 'very-sad' | 'sleeping' = 'happy';
	let quokkaName = 'Quokka';

	let isJumping = false;
	let isEating = false;
	let isWaving = false;

	onMount(() => {
		const savedQuokka = localStorage.getItem('quokkaPet');
		if (savedQuokka) {
			const data = JSON.parse(savedQuokka);
			happiness = data.happiness || 100;
			hunger = data.hunger || 100;
			energy = data.energy || 100;
			lastInteraction = data.lastInteraction || Date.now();
			quokkaName = data.name || 'Quokka';
		}

		setInterval(updateQuokka, 1000);
	});

	function updateQuokka() {
		const now = Date.now();
		const timeDiff = (now - lastInteraction) / 1000;

		if (!isSleeping) {
			happiness = Math.max(0, happiness - timeDiff * 0.5);
			hunger = Math.max(0, hunger - timeDiff * 0.3);
			energy = Math.max(0, energy - timeDiff * (10 - hunger / 10));
		} else {
			energy = Math.min(100, energy + timeDiff * Math.round(Math.random() * 5));
		}

		updateMood();
		saveQuokka();
		lastInteraction = now;
	}

	function updateMood() {
		const avg = (happiness + hunger + energy) / 3;
		if (avg > 80) currentMood = 'happy';
		else if (avg > 50) currentMood = 'content';
		else if (avg > 25) currentMood = 'sad';
		else currentMood = 'very-sad';
	}

	function feed() {
		if (!isEating && !isSleeping) {
			isEating = true;
			hunger = Math.min(100, hunger + 30);
			happiness = Math.min(100, happiness + 10);
			updateMood();
			saveQuokka();

			setTimeout(() => {
				isEating = false;
			}, 2000);
		}
	}

	function play() {
		if (!isJumping && !isSleeping && energy > 20) {
			isJumping = true;
			happiness = Math.min(100, happiness + 25);
			energy = Math.max(0, energy - 15);
			updateMood();
			saveQuokka();

			setTimeout(() => {
				isJumping = false;
			}, 1500);
		}
	}

	function sleep() {
		isSleeping = !isSleeping;
		if (isSleeping) {
			currentMood = 'sleeping';
		} else {
			updateMood();
		}
		saveQuokka();
	}

	function pet() {
		if (!isWaving && !isSleeping) {
			isWaving = true;
			happiness = Math.min(100, happiness + 15);
			updateMood();
			saveQuokka();

			setTimeout(() => {
				isWaving = false;
			}, 1000);
		}
	}

	function saveQuokka() {
		const data = {
			happiness,
			hunger,
			energy,
			lastInteraction: Date.now(),
			name: quokkaName
		};
		localStorage.setItem('quokkaPet', JSON.stringify(data));
	}
</script>

<Banner />
<Navbar currentPage="quokka" />

<div class="flex min-h-screen flex-col items-center justify-center px-8">
	<div class="w-full max-w-2xl">
		<div class="mb-8 text-center">
			<h1 class="mb-2 text-4xl font-bold text-gray-800">Your Quokka Friend</h1>
			<p class="text-gray-600">Take care of your virtual quokka!</p>
		</div>
		<div class="mb-8 flex justify-center">
			<div class="relative">
				<button
					class="relative"
					on:click={(e) => {
						if (e.ctrlKey || e.metaKey) {
							feed();
						} else if (isSleeping) {
							sleep();
						} else {
							pet();
						}
					}}
					on:contextmenu={(e) => {
						e.preventDefault();
						if (e.ctrlKey || e.metaKey) {
							play();
						} else if (!isSleeping) {
							sleep();
						}
					}}
				>
					{#key currentMood}
						<QuokkaIllustration mood={currentMood} {isJumping} {isSleeping} />
					{/key}
				</button>
				<div
					class="absolute -top-4 left-1/2 -translate-x-1/2 rounded-full bg-white px-3 py-1 text-sm font-medium shadow-md"
				>
					{#if currentMood === 'happy'}
						😊 Happy
					{:else if currentMood === 'content'}
						🙂 Okayish
					{:else if currentMood === 'sad'}
						😔 Sad
					{:else if currentMood === 'very-sad'}
						😢 Very Sad
					{:else if currentMood === 'sleeping'}
						😴 Sleeping
					{/if}
				</div>
			</div>
		</div>
		<div class="mb-8 grid grid-cols-3 gap-4">
			<div class="rounded-lg p-4 text-center">
				<div class="h-2 w-full rounded-full bg-gray-400">
					<div
						class="h-2 rounded-full bg-yellow-400 transition-all duration-300"
						style="width: {happiness}%"
					></div>
				</div>
				<div class="mt-1 text-lg font-bold text-gray-800">{Math.round(happiness)}%</div>
				<div class="mb-2 text-sm font-medium text-gray-600">Happiness</div>
			</div>

			<div class="rounded-lg p-4 text-center">
				<div class="h-2 w-full rounded-full bg-gray-400">
					<div
						class="h-2 rounded-full bg-orange-400 transition-all duration-300"
						style="width: {hunger}%"
					></div>
				</div>
				<div class="mt-1 text-lg font-bold text-gray-800">{Math.round(hunger)}%</div>
				<div class="mb-2 text-sm font-medium text-gray-600">Hunger</div>
			</div>

			<div class="rounded-lg p-4 text-center">
				<div class="h-2 w-full rounded-full bg-gray-400">
					<div
						class="h-2 rounded-full bg-blue-400 transition-all duration-300"
						style="width: {energy}%"
					></div>
				</div>
				<div class="mt-1 text-lg font-bold text-gray-800">{Math.round(energy)}%</div>
				<div class="mb-2 text-sm font-medium text-gray-600">Energy</div>
			</div>
		</div>
		<div class="mb-6 grid grid-cols-2 gap-4">
			<button
				on:click={feed}
				disabled={isEating || isSleeping}
				class="rounded-lg bg-green-500 px-6 py-3 font-medium text-white transition-all duration-200 hover:bg-green-600 disabled:cursor-not-allowed disabled:opacity-50"
			>
				{isEating ? 'Eating...' : 'Feed'}
			</button>

			<button
				on:click={play}
				disabled={isJumping || isSleeping || energy < 20}
				class="rounded-lg bg-blue-500 px-6 py-3 font-medium text-white transition-all duration-200 hover:bg-blue-600 disabled:cursor-not-allowed disabled:opacity-50"
			>
				{isJumping ? 'Playing...' : 'Play'}
			</button>

			<button
				on:click={sleep}
				class="rounded-lg bg-purple-500 px-6 py-3 font-medium text-white transition-all duration-200 hover:bg-purple-600"
			>
				{isSleeping ? 'Wake Up' : 'Sleep'}
			</button>
			<button
				on:click={pet}
				disabled={isWaving || isSleeping}
				class="rounded-lg bg-pink-500 px-6 py-3 font-medium text-white transition-all duration-200 hover:bg-pink-600 disabled:cursor-not-allowed disabled:opacity-50"
			>
				{isWaving ? 'Petting...' : 'Pet'}
			</button>
		</div>
	</div>
</div>
