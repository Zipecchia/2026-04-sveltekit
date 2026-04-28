<script>
	import favicon from '$lib/assets/favicon.svg';
	import ThemeToggle from '$lib/components/ThemeToggle.svelte';

	import "$lib/styles/reset.css";
	import "$lib/styles/tokens.css";

	let { children } = $props();

	// Theme management
	let theme = $state('dark');

	function toggleTheme() {
		theme = theme === 'dark' ? 'light' : 'dark';
	}
</script>

<svelte:head>
	<link rel="icon" href={favicon} />

	<!--Font Georama-->
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
<link href="https://fonts.googleapis.com/css2?family=Georama:ital,wght@0,100..900;1,100..900&family=Merriweather:ital,opsz,wght@0,18..144,300..900;1,18..144,300..900&family=Montserrat:ital,wght@0,100..900;1,100..900&family=Orbitron:wght@400..900&display=swap" rel="stylesheet">
</svelte:head>

<main data-theme={theme}>
	<header>
		<ThemeToggle {theme} {toggleTheme} />
	</header>

	{@render children()}
</main>
