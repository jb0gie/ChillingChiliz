<script>
	import { TwitterLogo, GithubLogo, DiscordLogo } from 'radix-icons-svelte';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu';
	import { Button } from '$lib/components/ui/button';
	import LightSwitch from './LightSwitch.svelte';
	import NavBarSheet from './NavBarSheet.svelte';
	import { cameraControls } from '../../stores';
	import logo from './logo.png';
	//Styling
	const headStyle =
		'supports-[backdrop-filter]:bg-background/60 sticky top-0 z-40 w-full border-b bg-background/95 shadow-sm backdrop-blur';
	const navIcon =
		'inline-flex items-center justify-center font-medium whitespace-nowrap transition-colors focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring disabled:pointer-events-none disabled:opacity-50 hover:bg-accent hover:text-accent-foreground h-8 rounded-md text-xs w-9 px-0';
	const navItem = 'transition-colors hover:text-foreground/80 text-foreground/60';
	//Locals
	let showStatusBar = true;
	let showActivityBar = false;
	let showPanel = false;

	//Camera setup
	let camera;
	$: if ($cameraControls) {
		camera = $cameraControls._camera;
	}

	function goHome(event) {
		$cameraControls.reset(true);
	}
</script>

<header class={headStyle}>
	<div class="container flex h-14 items-center">
		<div class="mr-4 hidden md:flex">
			<nav class="relative py-2 flex items-center space-x-6 text-sm font-medium">
				<button class="mr-6 flex items-center space-x-2" on:click={goHome}>
					<img src={logo} alt="" class="w-10" />
				</button>
				<!-- WORLD NAVIGATION DROPDOWN -->
				<DropdownMenu.Root>
					<DropdownMenu.Trigger asChild let:builder>
						<Button variant="link" class={navItem} builders={[builder]}>Explore</Button>
					</DropdownMenu.Trigger>
					<DropdownMenu.Content class="w-auto">
							<DropdownMenu.Item on:click={goHome}>
								<DropdownMenu.Label>Home</DropdownMenu.Label>
							</DropdownMenu.Item>
						<DropdownMenu.Separator />
						<a href="/about" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>About</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="/services" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>Tokenomics</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="/events" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>FAQ</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
					</DropdownMenu.Content>
				</DropdownMenu.Root>
				<!-- TEAM DROPDOWN -->
				<DropdownMenu.Root>
					<DropdownMenu.Trigger asChild let:builder>
						<Button variant="link" class={navItem} builders={[builder]}>Team</Button>
					</DropdownMenu.Trigger>
					<DropdownMenu.Content class="w-auto">
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>Hoek</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>Don</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>Howie</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>Gary</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>Dr.Doge</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>koH</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
						<DropdownMenu.Separator />
						<a href="" class={navItem}>
							<DropdownMenu.Item>
								<DropdownMenu.Label>b0gie</DropdownMenu.Label>
							</DropdownMenu.Item>
						</a>
					</DropdownMenu.Content>
				</DropdownMenu.Root>
			</nav>
		</div>

		<NavBarSheet />

		<div class="flex flex-1 items-center justify-between space-x-2 sm:space-x-4 md:justify-end">
			<div class="w-full flex-1 md:w-auto md:flex-none" data-svelte-h="svelte-1eg3ung" />
			<nav class="flex items-center space-x-1">
				<a href="https://github.com/anentrypoint" target="_blank" rel="noreferrer">
					<div class={navIcon}>
						<GithubLogo class="h-4 w-4" />
						<span class="sr-only" data-svelte-h="svelte-11yow7k">GitHub</span>
					</div>
				</a>
				<a href="https://discord.com/invite/xp3VwS5ySF" target="_blank" rel="noreferrer">
					<div class={navIcon}>
						<DiscordLogo class="h-4 w-4" />
						<span class="sr-only" data-svelte-h="svelte-11yow7k">Discord</span>
					</div>
				</a>
				<a href="https://x.com/3planetstudio" target="_blank" rel="noreferrer">
					<div class={navIcon}>
						<TwitterLogo class="h-4 w-4" />
						<span class="sr-only" data-svelte-h="svelte-ym26he">Twitter</span>
					</div>
				</a>
				<LightSwitch />
			</nav>
		</div>
	</div>
</header>
