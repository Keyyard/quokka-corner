<script lang="ts">
	import Banner from '../../components/Banner.svelte';
	import Navbar from '../../components/Navbar.svelte';
	import { onMount } from 'svelte';

	onMount(() => {
		const urlParams = new URLSearchParams(window.location.search);
		const secretParam = urlParams.get('secret');

		if (secretParam === 'true') {
			localStorage.setItem('quokkaSecret', 'true');
		}
	});
</script>

<Banner />
<Navbar currentPage="status" />
<section class="flex justify-center px-4 pt-24">
	<div class="flex flex-col gap-6">
		<div class="text-3xl font-bold">Their Status</div>
		<div class="max-w-2xl space-y-6 text-gray-700">
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Vulnerable!</h3>
				<p>
					Quokkas are already small in number and found mainly on just 2 islands. And above all,
					they have been in the <a
						href="https://www.iucnredlist.org/species/20165/258663635"
						class="text-blue-500 underline underline-offset-4 hover:decoration-wavy">vulnerable</a
					> region of the IUCN Red List with a decreasing population trend. These little fur balls are
					protected in Australia - the only place they are found.
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Wildfire</h3>
				<p>
					A large wildfire that raged across southwest Australia in 2015 devastated a significant
					population of mainland quokkas. The Northcliffe fire burnt 98,000 hectares. Today, around
					10,000 Quokkas live on Rottnest Island, with very small populations also surviving in the
					mainland's south-west forests such as those near Northcliffe. While they're doing
					relatively well on the islands, mainland populations face much greater threats and
					continue to decline.
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Climate change</h3>
				<p>
					As southwest of Western Australia dries due to climate change, there will be more habitat
					loss at the quokka's expense. Mainland populations have been historically restricted to
					areas with an annual average rainfall greater than 700mm and their current distribution is
					almost completely confined to the 1000mm rainfall isohyet (for those of us who are less
					into geography this simply means an imaginary line on a map connecting all the points
					having same amount of rainfall in a given period).
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Habitat loss</h3>
				<p>
					Following extensive population declines in the 20th century, by 1992, the quokka's
					distribution on the mainland had been reduced by more than 50% to an area of about 17,800
					km&sup2; from an original 41,200 km&sup2;. Their vulnerable status was a result of this as
					well as predation by larger and feral animals such as foxes and cats and several other
					factors.
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Threat from predators</h3>
				<p>
					Predators like the fox which was introduced in Australia for hunting purposes are a major
					threat to cute little quokkas as they evolved without these preadtors and thus lack the
					required defense strategies. Besides foxes, feral cats, also pose a threat to the species.
				</p>
			</div>
		</div>
		<div class="flex items-center justify-between gap-8 pt-6 pb-12 text-center">
			<div class="flex flex-col items-center">
				<div class="text-2xl font-semibold text-red-600">50%+</div>
				<div class="text-sm text-gray-500">Population Decline</div>
			</div>
			<div class="flex flex-col items-center">
				<div class="text-2xl font-semibold text-red-600">1996</div>
				<div class="text-sm text-gray-500">Vulnerable Since</div>
			</div>
			<div class="flex flex-col items-center">
				<div class="text-2xl font-semibold text-red-600">High Risk</div>
				<div class="text-sm text-gray-500">Extinction Risk</div>
			</div>
		</div>
	</div>
</section>
