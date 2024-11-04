<script>
	import { T } from '@threlte/core';
	import { Float, OrbitControls } from '@threlte/extras';
</script>

<T.PerspectiveCamera
makeDefault
position={[0, 0, 7]}
oncreate={(ref) => {
	ref.lookAt(0, 0, 0);
}}
>
<OrbitControls />
</T.PerspectiveCamera>

<T.DirectionalLight position={[10, 0, 50]} />

<Float
	position.y={-1}
	rotationIntensity={[0, 0.5, 0]}
	rotationSpeed={1}
	floatIntensity={1}
	floatingRange={[-0.2, 0.2]}
>
	<T.Mesh>
		<T.IcosahedronGeometry args={[1, 10]} />
		<T.MeshStandardMaterial color="#cc1100" metalness={0.5} roughness={0.5} />
	</T.Mesh>
</Float>

<Float
	position.y={-1}
    position.x={-3}
	rotationIntensity={[2, 2, 2]}
	rotationSpeed={1}
	floatIntensity={1}
	floatingRange={[-0.2, 0.2]}
>
	<T.Mesh>
		<T.BoxGeometry args={[1, 1.5, 1]} />
		<T.MeshToonMaterial color="#0077cc" />
	</T.Mesh>
</Float>

<Float
	position.y={-1}
    position.x={3}
	rotationIntensity={[2, 2, 2]}
	rotationSpeed={1}
	floatIntensity={1}
	floatingRange={[-0.2, 0.2]}
>
	<T.Mesh>
		<T.TorusKnotGeometry args={[0.7, 0.2, 200, 16]} />
		<T.MeshPhysicalMaterial color="#11cc00" roughness={1.0} clearcoat={1} />
	</T.Mesh>
</Float>
