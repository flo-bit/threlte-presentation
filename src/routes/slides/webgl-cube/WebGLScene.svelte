<script>
	import { T } from "@threlte/core";
	import { Float, OrbitControls } from "@threlte/extras";

    import * as THREE from "three";

    const geometry = new THREE.BufferGeometry();

// create a simple square shape. We duplicate the top left and bottom right
// vertices because each vertex needs to appear once per triangle.
const vertices = new Float32Array( [
    0.0,  1.0, 0.0,  // Top point
           -1.0, -1.0, 0.0,  // Bottom left
            1.0, -1.0, 0.0,  // Bottom right
] );

// itemSize = 3 because there are 3 values (components) per vertex
geometry.setAttribute( 'position', new THREE.BufferAttribute( vertices, 3 ) );
</script>

<T.PerspectiveCamera makeDefault position={[0, 3, 7]}>
    <OrbitControls />
</T.PerspectiveCamera>

<Float rotationIntensity={[0, 5, 1]} rotationSpeed={3}>
    <T.Mesh>
        <T.BoxGeometry args={[2, 2, 2]}/>
        <T.MeshBasicMaterial color="red" />
    </T.Mesh>
</Float>