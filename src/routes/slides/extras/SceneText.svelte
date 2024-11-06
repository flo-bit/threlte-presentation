<script lang="ts">
	import { T } from '@threlte/core';
	import { Text3DGeometry, Float } from '@threlte/extras';
</script>

<T.DirectionalLight position={[10, 5, 10]} intensity={4} />

<Float rotationIntensity={[0, 1, 0]} rotationSpeed={3}>
<T.Mesh position.x={-7} position.y={-2.5} position.z={-3}>
	<Text3DGeometry
		font={'/fonts/Inter-semibold.blob'}
		text={'hello'}
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
