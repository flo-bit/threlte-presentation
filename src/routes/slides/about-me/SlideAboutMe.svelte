<script>
	// Depth3D example
	import Depth3D from '$lib/Depth3D';
	import MySlide from '$lib/MySlide.svelte';
</script>

<MySlide>
	<div class="flex gap-4 p-16 items-center justify-center">
		<div class="h-96 aspect-square">
			<!-- will adjust to the parents size/position -->
			<Depth3D
				image={{
					image: '/me/me.png',
					depth: '/me/me-depth.png'
				}}
                rounded
			/>
		</div>
		<div class="flex flex-col gap-16 justify-start">
			<div class="text-7xl font-bold">About Me</div>

			<div class="flex flex-col gap-4 items-start text-left">
                <div class="text-4xl">- Florian, 27 years old</div>
                <div class="text-4xl">- Started programming as a teenager with OpenGL and C</div>
                <div class="text-4xl">- Studying CS as TUB</div>
                <div class="text-4xl">- ❤️ svelte, the web and 3d</div>
                <div class="text-4xl">- work for a startup</div>
                <div class="text-4xl">- some svelte in production</div>
            </div>
		</div>
	</div>
</MySlide>
