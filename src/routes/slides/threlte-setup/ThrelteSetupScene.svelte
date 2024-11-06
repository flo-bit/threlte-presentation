<script lang="ts">
	import { T, useTask } from '@threlte/core';

	import { interactivity } from '@threlte/extras';
	import { spring } from 'svelte/motion';
	interactivity();
	const scale = spring(1);

	let { step }: { step: number } = $props();

	let rotation = $state(0);
	useTask((delta) => {
		if (step > 5) rotation += delta;
	});
</script>

{#if step > 1}
	<T.PerspectiveCamera
		makeDefault
		position={[10, 10, 10]}
		oncreate={(ref) => {
			ref.lookAt(0, 0, 0);
		}}
	></T.PerspectiveCamera>
{/if}

{#if step > 3}
	<T.DirectionalLight position={[2, 10, 50]} />
{/if}

<T.Mesh
	rotation.y={rotation}
	scale={$scale}
	onpointerenter={() => {
		if (step > 4) scale.set(1.5);
	}}
	onpointerleave={() => scale.set(1)}
>
	<T.BoxGeometry args={[2, 2, 2]} />
	{#if step > 2}
		<T.MeshStandardMaterial color="red" />
	{:else}
		<T.MeshBasicMaterial color="red" />
	{/if}
</T.Mesh>