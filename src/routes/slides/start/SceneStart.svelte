<script>
	import { T, useTask } from '@threlte/core';
	import { interactivity } from '@threlte/extras';
	import { spring } from 'svelte/motion';

	import { Environment, Float, OrbitControls, Text3DGeometry, Stars } from '@threlte/extras';
	import Nebula from './Nebula.svelte';
	import CustomRenderer from './CustomRenderer.svelte';

	interactivity();
	const scale = spring(1);
	let rotation = 0;
	useTask((delta) => {
		rotation += delta;
	});
</script>

<Float rotationIntensity={[0, 0.5, 0]} rotationSpeed={1}>
	<T.PerspectiveCamera
		makeDefault
		position={[0, 2, 20]}
		oncreate={(ref) => {
			ref.lookAt(0, 0, 0);
		}}
	>
		<OrbitControls />
	</T.PerspectiveCamera>
</Float>

<T.DirectionalLight position={[0, 5, 10]} color="#ffff00" intensity={2} />

<Float rotationIntensity={[0, 1, 0]} rotationSpeed={1} floatingRange={[-7, -5]} speed={3}>
	<T.Mesh position.x={-12.5}>
		<Text3DGeometry
			font={'/fonts/Inter-semibold.blob'}
			text={'Threlte'}
			bevelEnabled={true}
			bevelOffset={0.0}
			bevelSegments={50}
			bevelSize={0.1}
			bevelThickness={0.2}
			depth={1}
			height={1}
			size={5}
		/>
		<T.MeshStandardMaterial color="#FD3F00" metalness={0.9} roughness={0.1} />
	</T.Mesh>
</Float>

<Environment files="/hdr/aerodynamics_workshop_1k.hdr" />

<Stars />

<Nebula />

<!-- <CustomRenderer /> -->
