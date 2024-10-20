<script lang="ts">
	import { Canvas } from '@threlte/core';
	import Scene from './SceneStart.svelte';
	import MySlide from '$lib/MySlide.svelte';
	import { Code } from '@animotion/core';

	let { show }: { show?: boolean } = $props();
</script>

<MySlide {show}>
	<div
		class="text-8xl font-bold max-w-4xl mx-auto absolute top-16 z-20 left-0 right-0 text-orange-200"
	>
		Building awesome 3D web experiences with
	</div>
	<div class="absolute inset-0 h-full w-full z-10">
		<Canvas>
			<Scene />
		</Canvas>
	</div>

	<div class="absolute inset-0 h-full w-full bg-black z-0"></div>
</MySlide>
