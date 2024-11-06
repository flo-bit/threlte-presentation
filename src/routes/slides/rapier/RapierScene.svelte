<script>
	import { T } from '@threlte/core';
	import { OrbitControls } from '@threlte/extras';
	import { AutoColliders, Debug, RigidBody } from '@threlte/rapier';
</script>

<T.PerspectiveCamera
	makeDefault
	position={[0, 2, 20]}
	oncreate={(ref) => {
		ref.lookAt(0, 0, 0);
	}}
>
	<OrbitControls />
</T.PerspectiveCamera>

<T.DirectionalLight position={[10, 10, 10]} />

<AutoColliders>
	<T.Mesh position.x={-5} rotation.z={-0.5} position.y={3}>
		<T.BoxGeometry args={[10, 0.5, 5]} />
		<T.MeshStandardMaterial color="#414141" />
	</T.Mesh>

	<T.Mesh position.x={3} rotation.z={0.3} position.y={-2}>
		<T.BoxGeometry args={[10, 0.5, 5]} />
		<T.MeshStandardMaterial color="#414141" />
	</T.Mesh>

	<T.Mesh position.x={-6} rotation.z={-0.4} position.y={-5}>
		<T.BoxGeometry args={[10, 0.5, 5]} />
		<T.MeshStandardMaterial color="#414141" />
	</T.Mesh>
</AutoColliders>

{#each new Array(100) as _}
	<RigidBody>
		<AutoColliders density={100}>
			<T.Mesh position.y={10 + Math.random() * 20} position.x={-5 + Math.random() * 2}>
				<T.IcosahedronGeometry args={[0.2, 10]} />
				<T.MeshStandardMaterial color={Math.random() * 0xffffff} />
			</T.Mesh>
		</AutoColliders>
	</RigidBody>
{/each}
