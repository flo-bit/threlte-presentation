<script lang="ts">
	import MySlide from '$lib/MySlide.svelte';
	import { Code, Action } from '@animotion/core';
	import { Canvas } from '@threlte/core';
	import ThrelteSetupScene from './ThrelteSetupScene.svelte';

	let code: ReturnType<typeof Code>;

	let step = $state(0);
</script>

<MySlide>
	<div class="mx-10 my-10 w-[600px] flex flex-col items-center justify-start h-full text-2xl">
		<h2 class="text-2xl font-semibold text-left w-full">Scene.svelte</h2>
		<Code
			bind:this={code}
			lang="svelte"
			theme="github-light"
			class="p-4 rounded-md m-4 inline-block w-full"
			code={`<script>
    import { T } from '@threlte/core'
<\/script>

<T.Mesh>
    <T.BoxGeometry />
    <T.MeshBasicMaterial color="red" />
</T.Mesh>`}
		/>

		<Action
			undo={() => {
				step = 0;
			}}
			do={() => {
				step = 1;
			}}
		/>
		<Action
			do={() => {
				// update the code
				code.update`<script>
    import { T } from '@threlte/core'
<\/script>

<T.PerspectiveCamera makeDefault position={[10, 10, 10]} 
    oncreate={(ref) => { ref.lookAt(0, 0, 0); }} />

<T.Mesh>
    <T.BoxGeometry />
    <T.MeshBasicMaterial color="red" />
</T.Mesh>`;
				step = 2;
			}}
		/>

		<Action
			do={() => {
				// update the code
				code.update`<script>
    import { T } from '@threlte/core'
<\/script>

<T.PerspectiveCamera makeDefault position={[10, 10, 10]} 
    oncreate={(ref) => { ref.lookAt(0, 0, 0); }} />

<T.Mesh>
    <T.BoxGeometry />
    <T.MeshStandardMaterial color="red" />
</T.Mesh>`;
				step = 3;
			}}
		/>

		<Action
			do={() => {
				// update the code
				code.update`<script>
    import { T } from '@threlte/core'
<\/script>

<T.PerspectiveCamera makeDefault position={[10, 10, 10]} 
    oncreate={(ref) => { ref.lookAt(0, 0, 0); }} />

<T.DirectionalLight position={[2, 10, 50]} />

<T.Mesh>
    <T.BoxGeometry />
    <T.MeshStandardMaterial color="red" />
</T.Mesh>`;
				step = 4;
			}}
		/>
		<Action
			do={() => {
				// update the code
				code.update`<script>
    import { T } from '@threlte/core'
    import { interactivity } from '@threlte/extras'
    import { spring } from 'svelte/motion'
    interactivity()
    const scale = spring(1)
<\/script>

<T.PerspectiveCamera makeDefault position={[10, 10, 10]} 
    oncreate={(ref) => { ref.lookAt(0, 0, 0); }} />

<T.DirectionalLight position={[2, 10, 50]} />

<T.Mesh 
  scale={$scale}
  onpointerenter={() => scale.set(1.5)}
  onpointerleave={() => scale.set(1)}>
    <T.BoxGeometry />
    <T.MeshStandardMaterial color="red" />
</T.Mesh>`;
				step = 5;
			}}
		/>

		<Action
			do={() => {
				// update the code
				code.update`<script>
    import { T, useTask } from '@threlte/core'
    import { interactivity } from '@threlte/extras'
    import { spring } from 'svelte/motion'
    interactivity()
    const scale = spring(1)

    let rotation = $state(0);
    useTask((delta) => {
        rotation += delta
    })
<\/script>

<T.PerspectiveCamera makeDefault position={[10, 10, 10]} 
    oncreate={(ref) => { ref.lookAt(0, 0, 0); }} />

<T.DirectionalLight position={[2, 10, 50]} />

<T.Mesh 
  rotation.y={rotation}
  scale={$scale}
  onpointerenter={() => scale.set(1.5)}
  onpointerleave={() => scale.set(1)}>
    <T.BoxGeometry />
    <T.MeshStandardMaterial color="red" />
</T.Mesh>`;
				step = 6;
			}}
		/>
	</div>

	<div class="w-1/2 h-full absolute top-0 bottom-0 right-0">
		{#if step > 0}
			<Canvas>
				<ThrelteSetupScene {step} />
			</Canvas>
		{/if}
	</div>
</MySlide>
