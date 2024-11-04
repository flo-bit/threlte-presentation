<script lang="ts">
	import { Canvas } from '@threlte/core';
	import MySlide from '$lib/MySlide.svelte';
	import { Action } from '@animotion/core';

	import Scene from './SceneMaterials.svelte';

	let { show }: { show?: boolean } = $props();

	let active = $state(false);
</script>

<MySlide {show}>
	<div
		class="text-8xl font-bold max-w-4xl mx-auto absolute top-16 z-20 left-0 right-0"
	>
        Prebuilt materials/objects
	</div>
	<div class="absolute inset-0 h-full w-full z-10">
		<Canvas>
				<Scene {active}/>
		</Canvas>
	</div>

	<Action
			do={() => {
				active = true;
			}}
		/>
</MySlide>
