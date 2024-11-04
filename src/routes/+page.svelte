<script>
	import { Presentation } from '@animotion/core';
	import SlideStart from './slides/start/SlideStart.svelte';
	import SlideTest from './slides/test/SlideTest.svelte';
	import SlideAboutMe from './slides/about-me/SlideAboutMe.svelte';
	import MySlide from '$lib/MySlide.svelte';
	import DemoSlide from '$lib/DemoSlide.svelte';
	import Title from '$lib/Title.svelte';
	import SceneMaterials from './slides/materials/SceneMaterials.svelte';
	import SlideMaterials from './slides/materials/SlideMaterials.svelte';
	import SlideSceneGraph from './slides/scene-graph/SlideSceneGraph.svelte';
</script>

<Presentation
	class="flex items-center justify-center min-h-screen"
	options={{ controls: true, progress: false, disableLayout: false, width: 1200, height: 700 }}
>
	<!-- <SlideStart show /> -->
	<MySlide />


	<SlideSceneGraph />

	<Title title="Why threlte?" />
	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4 text-left">
			<div class="text-5xl font-bold mb-16">Why threlte?</div>
			<div class="text-3xl">- thin wrapper around three.js</div>
			<div class="text-3xl">- easy integration into svelte(kit)</div>
			<div class="text-3xl">- component system: reusability, structure</div>
			<div class="text-3xl">- automatic scheduling, event handling, on-demand rendering, disposing of objects</div>
			<div class="text-3xl">- batteries included</div>
		</div>
	</MySlide>

	<Title title="Why three.js?" />
	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4">
			<div class="text-5xl font-bold mb-16">Why three.js?</div>
			<div class="text-3xl">- high level wrapper around webgl/webgpu</div>
			<div class="text-3xl">- cross platform support</div>
			<div class="text-3xl">- prebuilt shaders, geometries</div>
			<div class="text-3xl">- scene graph</div>
			<div class="text-3xl">- textures, animations, 3d models</div>
		</div>
	</MySlide>
	<SlideMaterials />

	<SlideAboutMe />
	<SlideTest />

	<Title title="Why 3D in the web?" />
	<DemoSlide iframe="https://clover-product-page.netlify.app/" title="Product showcase"/>
	<DemoSlide iframe="https://bruno-simon.com/" title="Captivating websites"/>
	<DemoSlide image="/vr.webp" title="VR glasses"/>
	<DemoSlide iframe="https://flo-bit.dev/ball-game/" title="Interactive games"/>


</Presentation>

<div class="absolute inset-0 w-full h-full bg-stone-900"></div>
