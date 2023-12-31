<script>
	import * as Sheet from '$lib/components/ui/sheet';
	import NavLogo from './NavLogo.svelte'
	import { cameraControls } from '../../stores';
	let side = 'left';

	//Camera setup
	let camera;
	$: if ($cameraControls) {
		camera = $cameraControls._camera;
	}

	function goHome(event) {
		$cameraControls.reset(true);
	}
</script>

<Sheet.Root>
	<Sheet.Trigger>
		<NavLogo />
	</Sheet.Trigger>
	<Sheet.Content {side}>
		<div class="p-4">
			<h1 class="text-2xl font-semibold">Chilling Chiliz</h1>
			<ul class="mt-4">
				<li class="mb-2">Home</li>
				<li class="mb-2">About</li>
				<li class="mb-2">Events</li>
				<li class="mb-2">Services</li>
				<li class="mb-2">Art</li>
				<li class="mb-2">Music</li>
			</ul>
		</div>
	</Sheet.Content>
</Sheet.Root>
