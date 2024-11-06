<script lang="ts">
	import { Environment, OrbitControls } from '@threlte/extras';
	import Barbarian from './Barbarian.svelte';
	import { T } from '@threlte/core';

	let { step }: { step: number } = $props();
</script>

<T.DirectionalLight position={[5, 5, 20]} />
<Barbarian
	currentAction={step > 2 ? 'Walking_A' : 'Idle'}
	leftHand={step > 3 ? 'Weapon' : 'none'}
	rightHand={step > 4 ? 'Mug' : 'none'}
/>

<Environment files="/hdr/aerodynamics_workshop_1k.hdr" />

<T.PerspectiveCamera makeDefault position.y={1} position.z={3} position.x={-2} fov={90}>
	<OrbitControls enableDamping />
</T.PerspectiveCamera>
