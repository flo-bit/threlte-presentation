<script lang="ts">
	import { Canvas } from '@threlte/core';
	import Scene from './SceneStart.svelte';
	import MySlide from '$lib/MySlide.svelte';
	import { Action } from '@animotion/core';
	import { World } from '@threlte/rapier';

	let { show }: { show?: boolean } = $props();

	let active = $state(false);
</script>

<MySlide {show}>
	<div
		class="text-8xl font-bold max-w-4xl mx-auto absolute top-16 z-20 left-0 right-0 text-orange-200"
	>
		Building awesome 3D web experiences with
	</div>
	<div class="absolute inset-0 h-full w-full z-10">
		<Canvas>
			<World gravity={[0, 0, 0]}>
				<Scene {active}/>
			  </World>
		</Canvas>
	</div>

	<div class="absolute inset-0 h-full w-full bg-black z-0"></div>

	<Action
			do={() => {
				active = true;
			}}
		/>
</MySlide>
