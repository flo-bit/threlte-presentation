<script lang="ts">
	import MySlide from '$lib/MySlide.svelte';
	import { Code, Action } from '@animotion/core';

	let { show }: { show?: boolean } = $props();
</script>

<MySlide {show}>
	<div class="mx-auto w-[600px] h-full text-4xl flex flex-col">

		<h1 class="text-6xl font-bold my-12">Scene Graph</h1>

		<div class="w-full text-left text-xl">
		<h3>House.svelte</h3>
		<Code
			lang="svelte"
			theme="github-light"
			class="p-4 rounded-md m-4"
			code={`<LivingRoom />
			<Bathroom />
			<LivingRoom />`}
		/>

		<h3>LivingRoom.svelte</h3>
		<Code
			lang="svelte"
			theme="github-light"
			class="p-4 rounded-md m-4"
			code={`<Table position={[1, 0, 2]} />
			<Chairs />
			<Carpet />`}
		/>

		<h3>Table.svelte</h3>
		<Code
			lang="svelte"
			theme="github-light"
			class="p-4 rounded-md m-4"
			code={`<Plate position={[0, 1, 0]} />
			<Leg position={[1, 0, 1]} />
			<Leg position={[-1, 0, 1]} />
			<Leg position={[1, 0, -1]} />
			<Leg position={[-1, 0, -1]} />
			
			<!-- stuff that's on the table -->
			<TableContent />`}
		/>
	</div>
	</div>
</MySlide>
