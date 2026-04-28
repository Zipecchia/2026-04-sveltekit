<script>
	let { theme, toggleTheme } = $props();
</script>

<button
	class="theme-toggle"
	onclick={toggleTheme}
	aria-label="Toggle theme"
>
	{#if theme === 'dark'}
		<span>🌙</span>
	{:else}
		<span>☀️</span>
	{/if}
</button>

<style>
	.theme-toggle {
		background: none;
		border: none;
		font-size: 24px;
		cursor: pointer;
		padding: var(--spacing-2);
		border-radius: var(--border-radius-sm);
		transition: background-color 0.2s ease;
		color: var(--color-content-primary);
	}

	.theme-toggle:hover {
		background-color: var(--color-background-primary);
		opacity: 0.8;
	}

	.theme-toggle:focus {
		outline: 2px solid var(--third-yellow-500);
		outline-offset: 2px;
	}
</style>