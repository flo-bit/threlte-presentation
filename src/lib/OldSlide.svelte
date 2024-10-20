<script lang="ts">
	import { Canvas } from '@threlte/core';
	import Scene from './Scene.svelte';
	import { getPresentation, Slide } from '@animotion/core';
	import { onMount } from 'svelte';

	let { index }: { index: number } = $props();

	export const changed = () => console.log('changed');

	onMount(() => {
		setTimeout(() => {
			let presentation = getPresentation();
			presentation.slides.on('slidechanged', (event) => {
				let dist = Math.abs(event.indexh - index);

				if (dist > 1) {
					show = false;
				} else {
					show = true;
				}
			});
		}, 500);
	});

	let show = $state(index > 1);
</script>

<Slide class="h-[500px] w-[10px] bg-green-100 relative">
	{#if show}
		<Canvas>
			<Scene />
		</Canvas>
	{/if}

	<div class="absolute bottom-1 right-1">{index}</div>
</Slide>
