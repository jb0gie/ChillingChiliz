<script>
	import { T } from '@threlte/core';
	import { cameraControls } from '../../stores';
	import CameraControls from '../CameraControls/CameraControls.svelte';
	
	const startPos = [64.5, 2, -64.5];

	let camera
	$: if ($cameraControls) {
		camera = $cameraControls._camera
		// $cameraControls.zoom(camera.zoom / 0.5, true)
	}
</script>

<T.PerspectiveCamera makeDefault position={startPos}
	on:create={({ ref }) => {
		ref.lookAt(0, 1, 0);
	}}
>
	<CameraControls
		enabled={false} 
		on:create={({ ref }) => {
			$cameraControls = ref;
			
		}}
	/>
</T.PerspectiveCamera>