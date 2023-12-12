<script>
	//Threlte
	import { T } from '@threlte/core';
	import { TransformControls } from '@threlte/extras';
	import { DirectionalLightHelper, BoxGeometry, MeshStandardMaterial } from 'three';
	//Static meshes (envirounment)
	import Ground from '../lib/components/Assets/ground.svelte';
	import Trees from '../lib/components/Assets/trees.svelte';
	import Road from '../lib/components/Assets/road.svelte';
	import Fence from '../lib/components/Assets/fence.svelte';
	//Buildings (point of interests)
	import Windmill from '../lib/components/Assets/windmill.svelte';
	import Greenhouse from '../lib/components/Assets/greenhouse.svelte';
	import Shed from '../lib/components/Assets/shed.svelte';
	//Camera
	import Camera from '../lib/components/Assets/camera.svelte';
	//Lights
	let dirLightHelpr = DirectionalLightHelper;
</script>

<!-- Camera -->
<Camera />
<!-- Lights -->
<T.DirectionalLight let:ref castShadow position={[0, 10, 10]} intensity={1}>
	<TransformControls
		object={ref}
		on:objectChange={() => {
			if (!dirLightHelpr) return;
			dirLightHelpr.update();
		}}
	/>
	<T.DirectionalLightHelper args={[ref]} bind:ref={dirLightHelpr} />
</T.DirectionalLight>
<T.AmbientLight intensity={0.3} />
<!-- Fog -->
<T.FogExp2 />

<T.GridHelper args={[50, 50]} />

<TransformControls translationSnap={1} position.y={1}>
	<T.Mesh geometry={new BoxGeometry(2, 2, 2)} material={new MeshStandardMaterial()} castShadow />
</TransformControls>

<Ground />
<Trees />
<Road />
<Fence />

<!-- IF OR EACH BLOCK i think goes here  -->

<Greenhouse />
<Windmill />
<Shed />
