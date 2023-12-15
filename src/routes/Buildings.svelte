<script>
	//Buildings
	import House from '../lib/components/Assets/house.svelte';
	import Shed from '../lib/components/Assets/shed.svelte';
	import Barn from '../lib/components/Assets/barn.svelte';
	import Outhouse from '../lib/components/Assets/outhouse.svelte';
	import Greenhouse from '../lib/components/Assets/greenhouse.svelte';
	import Garage from '../lib/components/Assets/garage.svelte';
	//Camera-Controls
	import { cameraControls, house, shed, barn, outHouse, greenHouse, garage } from '../lib/stores';
	let camera;
	$: if ($cameraControls) {
		camera = $cameraControls._camera;
	}
</script>

<House
	on:create={({ ref }) => {
		$house = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($house, true);
	}}
/>
<Shed
	on:create={({ ref }) => {
		$shed = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($shed, true);
	}}
/>
<Barn 
on:create={({ ref }) => {
		$barn = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($barn, true);
	}}
/>
<Outhouse 
on:create={({ ref }) => {
		$outHouse = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($outHouse, true);
	}}
/>
<Greenhouse
on:create={({ ref }) => {
		$greenHouse = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($greenHouse, true);
	}}
/>
<Garage 
on:create={({ ref }) => {
		$garage = ref;
	}}
	on:click={() => {
		$cameraControls.fitToBox($garage, true);
	}}
/>
