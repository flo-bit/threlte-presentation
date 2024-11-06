<script>
	import { T, useTask } from '@threlte/core';
	import { OrbitControls, Sky } from '@threlte/extras';

    let elevation = $state(0)
    useTask((delta) => {
        elevation += delta * 0.5;
    })
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

<Sky elevation={Math.sin(elevation) * 10 + 5}/>
