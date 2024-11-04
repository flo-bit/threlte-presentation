<script lang="ts">
	import MySlide from '$lib/MySlide.svelte';

    let { title } : { title: string } = $props();
</script>

<MySlide>
	<div class="h-full flex items-center justify-center">
		<div class="text-8xl font-bold">{title}</div>
	</div>
</MySlide>
