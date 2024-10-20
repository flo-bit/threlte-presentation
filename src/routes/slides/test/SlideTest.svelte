<script lang="ts">
	import MySlide from '$lib/MySlide.svelte';
	import { Code, Action } from '@animotion/core';

	let { show }: { show?: boolean } = $props();

	let code: ReturnType<typeof Code>;
</script>

<MySlide {show}>
	<div class="mx-auto w-[600px] h-full text-4xl">
		<Code
			bind:this={code}
			lang="svelte"
			theme="github-light"
			class="p-4 rounded-md m-4"
			code={`<script lang="ts">
	import MySlide from '$lib/MySlide.svelte';
	import { Code } from '@animotion/core';

	let { show }: { show?: boolean } = $props();
<\/script>

<MySlide {show}>
	<div class="mx-auto w-[900px] h-full">
		<Code
			lang="svelte"
			lines="1"
			code="..."
		/>
	</div>
</MySlide>`}
		/>

		<Action
			do={() => {
				code.selectLines`1`;
			}}
		/>
	</div>
</MySlide>
