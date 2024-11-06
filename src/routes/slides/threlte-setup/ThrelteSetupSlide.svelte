<script>
	import MySlide from '$lib/MySlide.svelte';
	import { Code } from '@animotion/core';
</script>

<MySlide>
	<div class="mx-auto w-[600px] flex justify-center items-center flex-col h-full text-2xl">
		<h1 class="text-4xl font-bold mb-6">Installing threlte</h1>

        <h2 class="text-2xl font-semibold text-left w-full">1. create svelte app</h2>
		<Code
			lang="bash"
			theme="github-dark"
			class="p-4 rounded-md m-4 inline-block w-full"
			code={`npx sv create threlte-demo`}
		/>
        <h2 class="text-2xl font-semibold text-left w-full">2. install three.js + threlte</h2>
		<Code
			lang="bash"
			theme="github-dark"
			class="p-4 rounded-md m-4 inline-block w-full"
			code={`npm install three @threlte/core@next @threlte/extras@next`}
		/>

        <h2 class="text-2xl font-semibold text-left w-full">3. edit +page.svelte</h2>
        <Code
			lang="svelte"
			theme="github-light"
			class="p-4 rounded-md m-4 inline-block w-full"
			code={`<!-- +page.svelte -->
<script>
    import { Canvas } from '@threlte/core'
    import Scene from './Scene.svelte'
<\/script>
<div style="width: 100%; height: 100%;">
    <Canvas>
        <Scene />
    </Canvas>
</div>`}
		/>

	</div>
</MySlide>
