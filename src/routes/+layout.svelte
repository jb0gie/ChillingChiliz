<script>
	import '../app.postcss';
	import { ModeWatcher } from 'mode-watcher';
	import NavBar from '../lib/components/NavBar/NavBar.svelte';
	import FootBar from '../lib/components/FootBar/FootBar.svelte';
	// SEO
	const metaDefaults = {
		title: 'Chilling Chiliz',
		description: 'Chill Chili',
		image: '../../static/favicon'
	};
	const meta = {
		title: metaDefaults.title,
		description: metaDefaults.description,
		image: metaDefaults.image,
		// Article
		article: { publishTime: '', modifiedTime: '', author: '' },
		// Twitter
		twitter: {
			title: metaDefaults.title,
			description: metaDefaults.description,
			image: metaDefaults.image
		}
	};
</script>

<svelte:head>
	<title>{meta.title}</title>
	<meta name="title" content={meta.title} />
	<meta name="description" content={meta.description} />
	<meta name="keywords" content={meta.description} />
	<meta name="author" content="b0gieman" />
	<meta property="og:site_name" content="Chilling Chiliz" />
	<meta property="og:type" content="website" />
	<!-- <meta property="og:url" content="https://chillingchiliz.com{$page.url.pathname}" /> -->
	<meta property="og:locale" content="en_US" />
	<meta property="og:title" content={meta.title} />
	<meta property="og:description" content={meta.description} />
	<meta property="og:image" content={meta.image} />
	<meta property="og:image:secure_url" content={meta.image} />
	<meta property="og:image:type" content="image/jpg" />
	<meta property="og:image:width" content="" />
	<!--FIX-->
	<meta property="og:image:height" content="" />
	<!--ALSO FIX-->
	<meta name="twitter:card" content="summary" />
	<meta name="twitter:site" content="@3PlanetStudio" />
	<meta name="twitter:creator" content="@3PlanetStudio" />
	<meta name="twitter:title" content={meta.twitter.title} />
	<meta name="twitter:description" content={meta.twitter.description} />
	<meta name="twitter:image" content={meta.twitter.image} />
</svelte:head>
<!-- DarkMode -->
<ModeWatcher />

<NavBar />

<slot />

<FootBar />