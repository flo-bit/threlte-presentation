<script lang="ts">
	import type { RigidBody as RapierRigidBody } from '@dimforge/rapier3d-compat';
	import { T, useTask } from '@threlte/core';
	import { Collider, RigidBody } from '@threlte/rapier';
	import type { Vector3 } from 'three';

	let { active, size, direction, ...others  } : {
		active: boolean;
		size: number;
		direction: Vector3;
		others: any;
	} = $props();

	useTask((delta) => {
		if(active) asteroid.applyImpulse(direction, true);
	});

	let asteroid: RapierRigidBody;
</script>

<T.Group {...others}>
	<RigidBody type={'dynamic'} bind:rigidBody={asteroid}>
		<Collider restitution={0.1} shape={'ball'} args={[size]} />
		<T.Mesh>
			<T.IcosahedronGeometry args={[size]} />
			<T.MeshStandardMaterial color="#331100" metalness={0.0} roughness={0.9} flatShading />
		</T.Mesh>
	</RigidBody>
</T.Group>
