<script>
	import { forwardEventHandlers, T, useThrelte } from '@threlte/core';
	//Camera controls
	import CameraControls from '../CameraControls/CameraControls.svelte'
	import { cameraControls, mesh } from '../../stores';
	// const { invalidate } = useThrelte();
	// const el = document.getElementById('int-target');
	// const component = forwardEventHandlers();
	const startPos = [0,3,60]
</script>

<T.PerspectiveCamera
	makeDefault
	position={startPos}
>
	<CameraControls
		on:create={({ ref }) => {
			$cameraControls = ref;
		}}
	/>
	<!-- <T.OrbitControls bind:this={$component} args={[ref, el]} on:change={invalidate} /> -->
</T.PerspectiveCamera>

<!-- EXAMPLE 
<T.OrthographicCamera
  zoom={80}
  position={[10, 10, 10]}
  makeDefault
  let:ref
>
  <T.OrbitControls
    bind:this={$component}
    args={[ref, el]}
    on:change={invalidate}
    enableZoom={false}
  />
</T.OrthographicCamera> -->
