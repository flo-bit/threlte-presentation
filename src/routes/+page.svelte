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

	import { Code } from '@animotion/core';
	import WebGlSlide from './slides/webgl-cube/WebGLSlide.svelte';
	import ThrelteSetupSlide from './slides/threlte-setup/ThrelteSetupSlide.svelte';
	import ThrelteSetupFilesSlide from './slides/threlte-setup/ThrelteSetupFilesSlide.svelte';

</script>

<Presentation
	class="flex items-center justify-center min-h-screen"
	options={{ controls: true, progress: false, disableLayout: false, width: 1200, height: 700 }}
>
	<!-- <SlideStart show /> -->
	<MySlide />

	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4">
			<div class="text-5xl font-bold mb-16">In this presentation:</div>
			<div class="text-3xl">- about me</div>
			<div class="text-3xl">- Why 3D in the web?</div>
			<div class="text-3xl">- webgl/webgpu</div>
			<div class="text-3xl">- three.js</div>
			<div class="text-3xl">- threlte intro</div>
			<div class="text-3xl">- threlte code</div>
			<div class="text-3xl">- threlte batteries</div>
			<div class="text-3xl">- links</div>
		</div>
	</MySlide>

	<SlideAboutMe />

	<Title title="Why 3D in the web?" />
	<DemoSlide iframe="https://clover-product-page.netlify.app/" title="Product showcase" />
	<DemoSlide iframe="https://next.junni.co.jp/" title="Eye-catcher" />
	<DemoSlide iframe="https://coastalworld.com/" title="Games" />
	<DemoSlide image="/vr.webp" title="Future: VR glasses?" />
	<DemoSlide image="/fun2.jpg" title="Fun" />

	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4">
			<div class="text-5xl font-bold mb-16">webgl/webgpu</div>
			<div class="text-3xl">- (3d) rendering api provided by browsers (using GPUs)</div>
			<div class="text-3xl">- more than 98% global suppport</div>
			<div class="text-3xl">- webgpu: new version</div>
			<div class="text-3xl">- 72% global suppport</div>
		</div>
	</MySlide>

	<Title title="Why three.js?" />

	<WebGlSlide />

	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4">
			<div class="text-5xl font-bold mb-8">Why three.js?</div>
			<div class="text-3xl font-semibold p-4 rounded-xl bg-red-300">short answer: webgl/webgpu very complicated/lots of code</div>
			<div class="text-3xl">- high level wrapper around webgl/webgpu</div>
			<div class="text-3xl">- cross platform support</div>

			<div class="text-3xl mt-4 font-semibold">- lots of in-built features:</div>

			<div class="text-3xl ml-4">- prebuilt shaders, geometries</div>
			<div class="text-3xl ml-4">- scene graph</div>
			<div class="text-3xl ml-4">- textures, animations, 3d models</div>
		</div>
	</MySlide>
	<SlideMaterials />
	<DemoSlide title="Scene Graph">
		<div class="absolute p-32 w-full h-full">
			<img
				src="/scene-graph.svg"
				alt=""
				class="absolute inset-0 w-full h-full object-contain pt-20 scale-90"
			/>
		</div>
	</DemoSlide>

	<Title title="Why threlte?" />
	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4 text-left">
			<div class="text-5xl font-bold mb-8">Why threlte?</div>
			<div class="text-3xl font-semibold">- super easy integration into svelte(kit) apps</div>

			<div class="text-3xl">- thin wrapper around three.js</div>
			<div class="text-3xl">- component system: reusability, works great with scene graph</div>
			<div class="text-3xl mt-4 font-semibold">- even more in-built features:</div>

			<div class="text-3xl ml-4">
				- automatic scheduling, event handling, on-demand rendering, disposing of objects
			</div>
			<div class="text-3xl ml-4">- "batteries included"</div>
		</div>
	</MySlide>

	<SlideSceneGraph />

	<Title title="Show me some code!" />

	<ThrelteSetupSlide />

	<ThrelteSetupFilesSlide />
</Presentation>

<div class="absolute inset-0 w-full h-full bg-stone-900"></div>
