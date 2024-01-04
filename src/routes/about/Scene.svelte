<script>
	//Threlte
	import { T, useThrelte, useTask } from '@threlte/core';
	import { interactivity, TransformControls } from '@threlte/extras';
	//ThreeJS
	import { DirectionalLightHelper, BoxGeometry, MeshStandardMaterial } from 'three';
	//Camera
	import Camera from '../../lib/components/Assets/camera.svelte';
	import { cameraControls, rockingChili, drivingChili, walkingChili, plant } from '../../lib/stores';
	//Static meshes (envirounment)
	import World from '../World.svelte';
	//Interactive meshes
	import Buildings from '../Buildings.svelte';
	import Plant from '../../lib/components/Assets/plant.svelte';
	//Animated meshes
	import Rockingchili from '../../lib/components/Assets/rockingchili.svelte';
	import Drivingchili from '../../lib/components/Assets/drivingchili.svelte';
	import Walkingchili from '../../lib/components/Assets/walkingchili.svelte';
	import Signpost from '../../lib/components/Assets/signpost.svelte';
	import Sign1 from '../../lib/components/Assets/sign1.svelte';
	import Sign2 from '../../lib/components/Assets/sign2.svelte';
	import Sign3 from '../../lib/components/Assets/sign3.svelte';
	import Sign4 from '../../lib/components/Assets/sign4.svelte';
	import Dancingchili from '../../lib/components/Assets/dancingchili.svelte';
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
<Signpost/>
<Sign1/>
<Sign2/>
<Sign3/>
<Sign4/>

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
<Dancingchili position={[65, 0, -58]} rotation.y={90}/>

<Drivingchili/>

<Walkingchili/>
