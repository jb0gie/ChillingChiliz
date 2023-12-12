<script>
	import { forwardEventHandlers, T, useThrelte } from '@threlte/core';
	
	const { invalidate } = useThrelte();
	const el = document.getElementById('int-target');
	const component = forwardEventHandlers();
</script>

<T.PerspectiveCamera fov={75} position={[10, 10, 10]} makeDefault let:ref>
	<T.OrbitControls 
		bind:this={$component}
		args={[ref, el]}
		on:change={invalidate}
	/>
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
