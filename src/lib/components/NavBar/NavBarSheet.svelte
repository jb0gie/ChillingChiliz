<script>
	import * as Sheet from '$lib/components/ui/sheet';
	import NavLogo from './NavLogo.svelte'
	let side = 'left';
</script>

<Sheet.Root>
	<Sheet.Trigger>
		<NavLogo />
	</Sheet.Trigger>
	<Sheet.Content {side}>
		<div class="p-4">
			<h1 class="text-2xl font-semibold">3rd Planet Studio</h1>
			<ul class="mt-4">
				<li class="mb-2"><a href="/home" class="block hover:text-indigo-400">Home</a></li>
				<li class="mb-2"><a href="/about" class="block hover:text-indigo-400">About</a></li>
				<li class="mb-2"><a href="/events" class="block hover:text-indigo-400">Events</a></li>
				<li class="mb-2"><a href="/services" class="block hover:text-indigo-400">Services</a></li>
				<li class="mb-2"><a href="/roster/art" class="block hover:text-indigo-400">Art</a></li>
				<li class="mb-2"><a href="/roster/music" class="block hover:text-indigo-400">Music</a></li>
			</ul>
		</div>
	</Sheet.Content>
</Sheet.Root>
