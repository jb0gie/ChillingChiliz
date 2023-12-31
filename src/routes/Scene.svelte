<script>
	//Threlte
	import { T, useThrelte, useTask } from '@threlte/core';
	import { interactivity, TransformControls } from '@threlte/extras';
	//ThreeJS
	import { DirectionalLightHelper, BoxGeometry, MeshStandardMaterial } from 'three';
	//Camera
	import Camera from '../lib/components/Assets/camera.svelte';
	import { cameraControls, rockingChili, drivingChili, walkingChili, plant } from '../lib/stores';
	//Static meshes (envirounment)
	import World from './World.svelte';
	//Interactive meshes
	import Buildings from './Buildings.svelte';
	import Plant from '../lib/components/Assets/plant.svelte';
	//Animated meshes
	import Rockingchili from '../lib/components/Assets/rockingchili.svelte';
	import Drivingchili from '../lib/components/Assets/drivingchili.svelte';
	import Walkingchili from '../lib/components/Assets/walkingchili.svelte';
	//Sky setup
	let exposure = 1;
	//Camera-Controls
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

<!-- Envirounment -->
<World />

<!-- POINTofINTERESTs -->
<Buildings />
<Plant
	on:create={({ ref }) => {
		$plant = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($plant, true);
	}}
/>
<Rockingchili
	on:create={({ ref }) => {
		$rockingChili = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($rockingChili, true);
	}}
/>
<Drivingchili
	on:create={({ ref }) => {
		$drivingChili = ref;
	}}
	on:pointermove={() => {
		$cameraControls.fitToBox($drivingChili, true);
	}}
/>
<Walkingchili
	on:create={({ ref }) => {
		$walkingChili = ref;
	}}
	on:pointermove={() => {
		$cameraControls.fitToBox($walkingChili, true);
	}}
/>
