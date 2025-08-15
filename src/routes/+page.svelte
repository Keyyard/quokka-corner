<script lang="ts">
	import Banner from '../components/Banner.svelte';
	import Navbar from '../components/Navbar.svelte';
	import quokka from '../lib/images/quokka.png';

	const quokkaFacts = [
		"They're related to kangaroos and wallabies",
		"Quokkas are known as the 'happiest animal on Earth' due to their friendly smile",
		'They can survive for months without drinking water, getting moisture from plants',
		'Quokkas are excellent climbers and can scale trees up to 6 feet high',
		"Baby quokkas are called joeys and stay in their mother's pouch for 6 months",
		'They can hop like kangaroos but prefer to walk on all fours',
		'Quokkas are primarily nocturnal and rest during the day',
		'They have a unique ability to store fat in their tails for survival during food shortages',
		'Quokkas are found only in Western Australia, mainly on Rottnest Island'
	];

	let currentFactIndex = $state(0);
	let currentFact = $derived(quokkaFacts[currentFactIndex]);

	function nextFact() {
		if (currentFactIndex === quokkaFacts.length - 1) {
			currentFactIndex = 0;
			localStorage.setItem('quokkaSecret', 'true');
			window.location.reload();
		} else {
			currentFactIndex = currentFactIndex + 1;
		}
	}
</script>

<Banner />
<Navbar currentPage="home" />
<section class="grid grid-cols-1 gap-12 overflow-hidden px-4 pt-36 md:grid-cols-2">
	<div class="flex items-center justify-center">
		<div class="w-56 rounded-xl bg-[#B5A181]">
			<div class="h-full w-[28rem]">
				<img src={quokka} alt="quokka portrait" class="-ml-28" />
			</div>
		</div>
	</div>
	<div class="flex flex-col items-center gap-3 text-center md:items-start md:text-left">
		<div class="text-2xl font-bold">The Quokka</div>
		<div class="text-gray-400 italic">Setonix brachyurus</div>
		<a
			href="/status?secret=true"
			class="w-fit cursor-default rounded-full bg-red-200 px-2 py-0.5 text-center text-xs text-red-400"
		>
			Vulnerable
		</a>
		<div class="text-gray-500 md:pr-8">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum, cumque. Nostrum itaque
			distinctio optio nisi placeat saepe aperiam, dolore vitae eveniet mollitia natus eius
			voluptate esse libero dicta. Ipsum, id? Lorem ipsum dolor sit amet consectetur adipisicing
			elit. Beatae, id non. Excepturi, possimus totam? Minus ex, voluptas dolor non, facilis iusto
			quam maiores tempore beatae, numquam officia nesciunt impedit neque?
		</div>
		<div class="flex w-full flex-wrap items-center justify-between pt-4 md:flex-nowrap md:pr-8">
			<div class="flex flex-col items-center">
				<div class="text-xl font-semibold">
					3 <span class="text-sm font-normal italic">kg</span>
				</div>
				<div class="text-sm text-gray-500">Weight</div>
			</div>
			<div class="flex flex-col items-center">
				<div class="text-xl font-semibold">
					40-54 <span class="text-sm font-normal italic">cm</span>
				</div>
				<div class="text-sm text-gray-500">Height</div>
			</div>
			<div class="flex flex-col items-center">
				<div class="text-xl font-semibold">
					66-85 <span class="text-sm font-normal italic">cm</span>
				</div>
				<div class="text-sm text-gray-500">Length</div>
			</div>
			<div class="flex flex-col items-center">
				<div class="text-xl font-semibold">
					10-15 <span class="text-sm font-normal italic">yrs</span>
				</div>
				<div class="text-sm text-gray-500">Lifespan</div>
			</div>
		</div>
		<section id="facts" class="pt-20">
			<div class="relative flex items-center gap-4">
				<div class="absolute -top-4 text-9xl opacity-30">&ldquo;</div>
				<div class="flex-1 px-14 py-6 font-semibold text-black">
					{currentFact}
				</div>
				<button
					onclick={nextFact}
					class="flex-shrink-0 cursor-pointer transition duration-300 ease-in-out hover:opacity-50"
				>
					{#if currentFactIndex === quokkaFacts.length - 1}
						<span class="icon-[mdi--refresh] text-3xl"></span>
					{:else}
						<span class="icon-[mdi--keyboard-arrow-right] text-4xl"></span>
					{/if}
				</button>
			</div>
		</section>
	</div>
</section>
