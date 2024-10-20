<script lang="ts">
	import { T } from '@threlte/core';
	import { useTexture } from '@threlte/extras';

	const map = useTexture('smoke.png');

	const redColors = [0xf87171, 0xfb923c, 0xfbbf24, 0xfacc15, 0xf472b6, 0xfb7185];
	// const blueColors = [0x34d399, 0x2dd4bf, 0x67e8f9, 0x0ea5e9, 0x60a5fa];
</script>

{#await map then value}
	<T.Group rotation.z={-0.5} position.x={-5} position.y={10}>
		{#each Array.from({ length: 30 }) as _, i}
			<T.Mesh
				position.z={-20 + Math.random()}
				position.x={Math.random() * 60 - 30}
				position.y={Math.random() * 50 - 30}
				rotation.z={Math.random() * 4}
				scale={(Math.random() * 8 + 1) * 4}
			>
				<T.PlaneGeometry />
				<T.MeshLambertMaterial
					map={value}
					color={redColors[Math.floor(Math.random() * redColors.length)]}
					transparent={true}
					opacity={0.3}
					depthWrite={false}
				/>
			</T.Mesh>
		{/each}
	</T.Group>
{/await}
