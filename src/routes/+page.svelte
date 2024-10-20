<script>
	import { Presentation } from '@animotion/core';
	import SlideStart from './slides/start/SlideStart.svelte';
	import SlideTest from './slides/test/SlideTest.svelte';
</script>

<Presentation
	class="flex items-center justify-center min-h-screen"
	options={{ controls: false, progress: false, disableLayout: false, width: 1200, height: 700 }}
>
	<SlideStart show />
	<SlideTest />
</Presentation>

<div class="absolute inset-0 w-full h-full bg-stone-900"></div>
