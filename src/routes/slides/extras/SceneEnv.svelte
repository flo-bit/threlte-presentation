<script>
	import { T } from '@threlte/core';
	import { Environment, OrbitControls } from '@threlte/extras';
</script>

<T.PerspectiveCamera
makeDefault
position.y={0}
position.z={-5}
fov={90}
>
<OrbitControls
  enableDamping
  autoRotate
  enablePan={false}
  enableZoom={false}
/>
</T.PerspectiveCamera>

<Environment files="/hdr/aerodynamics_workshop_1k.hdr" isBackground />
