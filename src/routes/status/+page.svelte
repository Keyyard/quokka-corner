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
		<div class="text-3xl font-bold">Vulnerable Status</div>
		<div class="max-w-2xl space-y-6 text-gray-700">
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Lorem ipsum</h3>
				<p>
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi suscipit fugit hic iure
					omnis qui non? Atque deserunt rerum illum. Doloribus alias magnam neque iste fugit autem
					deserunt similique est. Harum vel esse saepe nemo eum consectetur aperiam consequatur
					incidunt. Ducimus cumque possimus est amet dolores id excepturi omnis, ex, non et vitae
					impedit sit aliquid a? Quibusdam, at quam.
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Dolor sit</h3>
				<p>
					Lorem ipsum dolor sit amet, consectetur adipisicing elit. Corrupti quam aliquid possimus
					commodi vero dolorum blanditiis inventore numquam, mollitia nobis voluptatibus illo
					aperiam aspernatur nesciunt accusamus eius, sint maiores ad. Eos, placeat. Est
					repudiandae, nostrum non quo ipsam sapiente totam laudantium illum tempore rem earum
					possimus ullam repellat debitis modi fuga sit magni optio tenetur. Accusamus aperiam
					similique fugit ipsam!
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Amet consectetur</h3>
				<p>
					Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quisquam tenetur vitae officia!
					Molestias, deleniti assumenda at mollitia atque odio, labore cum expedita libero,
					distinctio ea accusantium temporibus provident amet quod. Labore animi maxime fugit quam
					ullam nihil ad sint, in inventore explicabo. Repellat nam saepe, quia tempora eius tempore
					nostrum? Eum qui et nulla, reiciendis sit ratione voluptate officia facere?
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Adipisicing elit</h3>
				<p>
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequatur deleniti, aliquid
					quisquam magni labore quae praesentium dolores quas corrupti porro incidunt officiis,
					nostrum ipsa qui. Veritatis iste minus provident fuga! Ea, quo obcaecati eum aperiam rerum
					facilis neque fuga repellendus qui laboriosam nulla perspiciatis vitae quibusdam
					voluptates provident dolore sit molestiae iste? Dolores aut obcaecati facilis, voluptatum
					deleniti natus velit!
				</p>
			</div>
			<div>
				<h3 class="mb-2 text-xl font-semibold text-black">Commodi suscipit</h3>
				<p>
					Lorem ipsum dolor sit, amet consectetur adipisicing elit. Similique illo doloribus sed,
					laborum architecto porro eos aliquam saepe, tempora nobis voluptatem! Voluptate labore
					expedita vero beatae doloribus enim hic? Iste? Pariatur et, doloremque maiores sint
					deserunt aspernatur incidunt. Veniam suscipit alias dignissimos, magnam omnis, animi saepe
					distinctio odio rerum vitae iste eaque debitis incidunt quo vero tempora ab esse
					voluptatem.
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
