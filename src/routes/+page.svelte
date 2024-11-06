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
	import { Canvas } from '@threlte/core';
	import SceneText from './slides/extras/SceneText.svelte';
	import SceneSky from './slides/extras/SceneSky.svelte';
	import SceneRefraction from './slides/extras/SceneRefraction.svelte';
	import SceneLines from './slides/extras/SceneEnv.svelte';
	import SceneStars from './slides/extras/SceneStars.svelte';
	import SceneGltf from './slides/gltf/SceneGLTF.svelte';
	import SceneEnv from './slides/extras/SceneEnv.svelte';
	import SlideGltf from './slides/gltf/SlideGLTF.svelte';
	import RapierSlide from './slides/rapier/RapierSlide.svelte';

</script>

<Presentation
	class="flex items-center justify-center min-h-screen"
	options={{ controls: true, progress: false, disableLayout: false, width: 1200, height: 700 }}
>
	<!-- <SlideStart show /> -->
	<MySlide />
	<DemoSlide image="/batteries.jpg" title="Batteries included" />

<RapierSlide />

	<SlideGltf />

	<MySlide>
		<div class="h-full flex items-start justify-start p-20 flex-col gap-4">
			<div class="text-5xl font-bold mb-8">other packages</div>
			<div class="text-3xl">@threlte/extras</div>
			<div class="text-3xl">@threlte/gltf</div>
			<div class="text-3xl">@threlte/rapier</div>
			<div class="text-3xl">@threlte/theater</div>
			<div class="text-3xl">@threlte/xr</div>
			<div class="text-3xl">@threlte/flex</div>
			<div class="text-3xl">@threlte/studio</div>
		</div>
	</MySlide>

	<MySlide>
		<div class="">
			<div class="mx-auto p-6 max-w-7xl">
			   <div class="grid grid-cols-1 gap-4 lg:grid-cols-6 lg:grid-rows-2">
				<div class="relative lg:col-span-3">
				  <div class="absolute inset-px rounded-lg bg-red-300 max-lg:rounded-t-[2rem] lg:rounded-tl-[2rem] overflow-hidden">
					<Canvas>
						<SceneText />
					</Canvas>

				  </div>


				  <div class="relative flex h-full flex-col overflow-hidden rounded-[calc(theme(borderRadius.lg)+1px)] max-lg:rounded-t-[calc(2rem+1px)] lg:rounded-tl-[calc(2rem+1px)]">
					<div class="p-5 pt-56">
						<p class="mt-2 text-2xl font-medium tracking-tight text-gray-950">Text3DGeometry</p>
					</div>
				  </div>
				  <div class="pointer-events-none absolute inset-px rounded-lg shadow ring-1 ring-black/5 max-lg:rounded-t-[2rem] lg:rounded-tl-[2rem]"></div>
				</div>
				<div class="relative lg:col-span-3">
				  <div class="absolute inset-px rounded-lg bg-white lg:rounded-tr-[2rem] overflow-hidden">
					<Canvas>
						<SceneSky />
					</Canvas>
				  </div>
				  <div class=" pointer-events-none relative flex h-full flex-col overflow-hidden rounded-[calc(theme(borderRadius.lg)+1px)] lg:rounded-tr-[calc(2rem+1px)]">
					<!-- <img class="h-80 object-cover object-left lg:object-right" src="https://tailwindui.com/plus/img/component-images/bento-01-releases.png" alt=""> -->
					<div class="p-5 pt-56">
						<p class="mt-2 text-2xl font-medium tracking-tight text-gray-950">Sky</p>
					  </div>
				  </div>
				  <div class="pointer-events-none absolute inset-px rounded-lg shadow ring-1 ring-black/5 lg:rounded-tr-[2rem]"></div>
				</div>
				<div class="relative lg:col-span-2">
				  <div class="absolute inset-px rounded-lg bg-white lg:rounded-bl-[2rem] overflow-hidden">
					<Canvas>
						<SceneRefraction />
					</Canvas>
				  </div>
				  <div class="relative flex h-full flex-col overflow-hidden rounded-[calc(theme(borderRadius.lg)+1px)] lg:rounded-bl-[calc(2rem+1px)]">
					<!-- <img class="h-80 object-cover object-left" src="https://tailwindui.com/plus/img/component-images/bento-01-speed.png" alt=""> -->
					<div class="p-5 pt-56">
						<p class="mt-2 text-2xl font-medium tracking-tight text-gray-950">MeshRefractionMaterial</p>
					  </div>
				  </div>
				  <div class="pointer-events-none absolute inset-px rounded-lg shadow ring-1 ring-black/5 lg:rounded-bl-[2rem]"></div>
				</div>
				<div class="relative lg:col-span-2">
				  <div class="absolute inset-px rounded-lg bg-black overflow-hidden">
					<Canvas>
						<SceneStars />
					</Canvas>
				  </div>
				  <div class="relative flex h-full flex-col overflow-hidden rounded-[calc(theme(borderRadius.lg)+1px)]">
					<!-- <img class="h-44 object-cover object-center" src="https://tailwindui.com/plus/img/component-images/bento-01-integrations.png" alt=""> -->
					<div class="p-5 pt-56">
						<p class="mt-2 text-2xl font-medium tracking-tight text-gray-50">FakeGlowMaterial</p>
					  </div>
				  </div>
				  <div class="pointer-events-none absolute inset-px rounded-lg shadow ring-1 ring-black/5"></div>
				</div>
				<div class="relative lg:col-span-2">
				  <div class="absolute inset-px rounded-lg bg-white max-lg:rounded-b-[2rem] lg:rounded-br-[2rem] overflow-hidden">
					<Canvas>
						<SceneEnv />
					</Canvas>
				  </div>
				  <div class="pointer-events-none relative flex h-full flex-col overflow-hidden rounded-[calc(theme(borderRadius.lg)+1px)] max-lg:rounded-b-[calc(2rem+1px)] lg:rounded-br-[calc(2rem+1px)]">
					<!-- <img class="h-80 object-cover object-center" src="https://tailwindui.com/plus/img/component-images/bento-01-network.png" alt=""> -->
					<div class="p-5 pt-56">
						<p class="mt-2 text-2xl font-medium tracking-tight text-gray-950 p-2 rounded-md bg-white/70">HDR Environment</p>
					  </div>
				  </div>
				  <div class="pointer-events-none absolute inset-px rounded-lg shadow ring-1 ring-black/5 max-lg:rounded-b-[2rem] lg:rounded-br-[2rem]"></div>
				</div>
			  </div>
			</div>
		  </div>
	</MySlide>

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
