<script lang="ts">
	import { Slide } from '@animotion/core';
	import type { Snippet } from 'svelte';

	type SlideProps = {
		children?: Snippet;
		in?: () => void;
		out?: () => void;
		animate?: boolean;
		animateEasing?: string;
		animateUnmatched?: boolean;
		animateId?: string;
		animateRestart?: boolean;
		background?: string;
		gradient?: string;
		image?: string;
		video?: string;
		iframe?: string;
		interactive?: boolean;
		transition?: 'none' | 'fade' | 'slide' | 'convex' | 'concave' | 'zoom';
		class?: string;

		title?: string;

		show?: boolean;
	};

	let { children, ...props }: SlideProps = $props();

	let show = $state(props.show ?? false);
</script>

<Slide
	class="w-full h-full overflow-visible p-2"
	{...props}
	in={() => {
		props.in?.();
		show = true;
	}}
	out={() => {
		props.out?.();

		setTimeout(() => {
			show = false;
		}, 200);
	}}
>
	<div
		class="bg-stone-100 h-full w-full relative rounded-xl overflow-hidden shadow-lg border border-stone-800"
	>
		{#if children && show}
			{@render children()}
		{/if}
	</div>
</Slide>
