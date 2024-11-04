<script lang="ts">
	import type { RigidBody as RapierRigidBody } from '@dimforge/rapier3d-compat';
	import { T, useTask } from '@threlte/core';
	import { Text3DGeometry, Suspense } from '@threlte/extras';
	import { RigidBody, AutoColliders } from '@threlte/rapier';

	let { letter, active, ...others }: { letter: string; active: boolean; others: any } = $props();

	let rigidBody: RapierRigidBody;

	useTask((delta) => {
		if (active) {
			rigidBody.applyImpulse(
				{ x: Math.random() * 0.01, y: Math.random() * 0.01, z: Math.random() * 0.01 },
				true
			);

			rigidBody.applyTorqueImpulse(
				{ x: Math.random() * 0.01, y: Math.random() * 0.01, z: Math.random() * 0.01 },
				true
			);
		}
	});
</script>

<T.Group {...others}>
	<RigidBody type={'dynamic'} bind:rigidBody>
		<AutoColliders restitution={0.1}>
			{#snippet children({ refresh })}
				<Suspense onload={refresh}>
					<T.Mesh position.x={-2} position.y={-2.5}>
						<Text3DGeometry
							font={'/fonts/Inter-semibold.blob'}
							text={letter}
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
				</Suspense>
			{/snippet}
		</AutoColliders>
	</RigidBody>
</T.Group>
