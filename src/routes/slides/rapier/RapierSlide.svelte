<script>

	import MySlide from "$lib/MySlide.svelte";
	import { Canvas } from "@threlte/core";
	import { World } from "@threlte/rapier";
	import RapierScene from "./RapierScene.svelte";

</script>

<MySlide>
    <h1 class="mx-auto py-16 text-4xl font-bold">Physics with rapier</h1>
	<div class="absolute inset-0 h-full w-full z-10">
		<Canvas>
			<World>
				<RapierScene />
			  </World>
		</Canvas>
	</div>
</MySlide>
