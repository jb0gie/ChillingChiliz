<script>
	import { Button } from "$lib/components/ui/button";
  import { Sun, Moon } from "radix-icons-svelte";
  import { toggleMode } from "mode-watcher";

  //Sky Presets
  const presets = {
		light: {
			turbidity: 10,
			rayleigh: 3,
			azimuth: 190,
			elevation: 0.7,
			mieCoefficient: 0.005,
			mieDirectionalG: 0.7,
			exposure: 0.37
		},
		dark: {
			turbidity: 20,
			rayleigh: 0.57,
			azimuth: 180,
			elevation: -5,
			mieCoefficient: 0.038,
			mieDirectionalG: 0,
			exposure: 0.26
		}
	};
  //Icons
	const sun = 'h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0'
	const moon = 'absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100'
</script>

<Button on:click={toggleMode} variant="outline" size="icon">
  <Sun class={sun} />
  <Moon class={moon} />
  <span class="sr-only">Toggle theme</span>
</Button>