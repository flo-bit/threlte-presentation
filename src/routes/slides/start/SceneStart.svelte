<script lang="ts">
	import { T, useTask } from '@threlte/core';
	import { interactivity } from '@threlte/extras';
	import { Environment, Float, OrbitControls, Stars } from '@threlte/extras';
	import Nebula from './Nebula.svelte';
	import Letter from './Letter.svelte';
	import Asteroid from './Asteroid.svelte';
	import { Vector3 } from 'three/src/math/Vector3.js';

	interactivity();
	
	let { active }: { active: boolean} = $props();
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

<T.Group position.x={-9} position.y={-3}>
	<Letter letter="T" {active} />
	<Letter letter="h" {active} position.x={4.5} />
	<Letter letter="r" {active} position.x={8.5} />
	<Letter letter="e" {active} position.x={11.1} />
	<Letter letter="l" {active} position.x={15} />
	<Letter letter="t" {active} position.x={16.5} />
	<Letter letter="e" {active} position.x={19} />
</T.Group>

<Asteroid {active} position={[0, 5, -40]} size={Math.random() * 3 + 1} direction={new Vector3(0, -2, 16)} />

<Environment files="/hdr/aerodynamics_workshop_1k.hdr" />

<Stars />

<Nebula />

<!-- <CustomRenderer /> -->
