<script lang="ts">
	import MySlide from './MySlide.svelte';

	let props: { iframe?: string; title?: string; image?: string, children?: any } = $props();
</script>

<MySlide>
	{#if props.image}
		<img src={props.image} alt="" class="absolute inset-0 w-full h-full object-cover" />
	{/if}

	{#if props.iframe}
		<iframe class="absolute inset-0 h-full w-full" title="" src={props.iframe}></iframe>
	{/if}
	{#if props.title}
		<div class="absolute top-2 left-2 right-2 pointer-events-none z-10">
			<div class="text-6xl text-white p-4 bg-black/70 backdrop-blur-sm rounded-xl">
				{props.title}
			</div>
		</div>
	{/if}
	
	{#if props.children}
		{@render props.children()}
	{/if}
</MySlide>
