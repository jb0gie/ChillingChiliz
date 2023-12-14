<script>
	//Threlte
	import { T, useThrelte, useTask } from '@threlte/core';
	import { interactivity, TransformControls } from '@threlte/extras';
	//ThreeJS
	import { DirectionalLightHelper, BoxGeometry, MeshStandardMaterial } from 'three';
	//Camera
	import Camera from '../lib/components/Assets/camera.svelte';
	import { cameraControls, mesh } from '../lib/stores';
	//Static meshes (envirounment)
	import Ground from '../lib/components/Assets/ground.svelte';
	import Trees from '../lib/components/Assets/trees.svelte';
	import Road from '../lib/components/Assets/road.svelte';
	import Fence from '../lib/components/Assets/fence.svelte';
	//Buildings (point of interests)
	import Windmill from '../lib/components/Assets/windmill.svelte';
	import Greenhouse from '../lib/components/Assets/greenhouse.svelte';
	import Shed from '../lib/components/Assets/shed.svelte';
	import Outhouse from '../lib/components/Assets/outhouse.svelte';
	import Props from '../lib/components/Assets/props.svelte';
	import Barn from '../lib/components/Assets/barn.svelte';
	import House from '../lib/components/Assets/house.svelte';
	import Garage from '../lib/components/Assets/garage.svelte';
	import Rockingchili from '../lib/components/Assets/rockingchili.svelte';
	import Drivingchili from '../lib/components/Assets/drivingchili.svelte';
	//Sky setup
	let exposure = 1;
	//Camera Setup
	let camera;
	$: if ($cameraControls) {
		camera = $cameraControls._camera;
	}

	const { renderer, invalidate } = useThrelte();

	$: {
		renderer.toneMappingExposure = exposure;
		invalidate();
	}

	interactivity();
</script>

<!-- Camera -->
<Camera />
<!-- Lights -->
<T.DirectionalLight let:ref castShadow position={[0, 10, 10]} intensity={1}>
	<!-- <TransformControls
		object={ref}
		on:objectChange={() => {
			if (!dirLightHelpr) return;
			dirLightHelpr.update();
		}}
	/>
	<T.DirectionalLightHelper args={[ref]} bind:ref={dirLightHelpr} /> -->
</T.DirectionalLight>
<T.AmbientLight intensity={0.3} />
<!-- Fog -->
<T.FogExp2 color="#cccccc" density={0.02} />

<!-- <T.GridHelper args={[50, 50]} /> -->

<!-- <TransformControls translationSnap={1} position.y={1}>
	<T.Mesh geometry={new BoxGeometry(2, 2, 2)} material={new MeshStandardMaterial()} castShadow />
</TransformControls> -->

<Ground />
<Trees />
<Fence />
<Road />
<Greenhouse />
<Windmill />
<Shed />
<Outhouse />
<Props />
<Barn />
<House />
<Garage />
<Rockingchili
	on:create={({ ref }) => {
		$mesh = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($mesh, true);
	}}
/>
<Drivingchili
	on:create={({ ref }) => {
		$mesh = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($mesh, true);
	}}
/>
