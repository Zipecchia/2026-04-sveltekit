<script lang="ts">
    // @ts-nocheck
    import "$lib/styles/reset.css";
    import "$lib/styles/tokens.css";

    let { children } = $props();
    let theme = $state<'dark' | 'light'>('dark');

    if (typeof window !== 'undefined') {
        const storedTheme = localStorage.getItem('theme');

        if (storedTheme === 'dark' || storedTheme === 'light') {
            theme = storedTheme;
        } else {
            theme = window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
        }
    }

    function toggleTheme() {
        theme = theme === 'dark' ? 'light' : 'dark';
        if (typeof window !== 'undefined') {
            localStorage.setItem('theme', theme);
        }
    }

    $effect(() => {
        document.documentElement.setAttribute('data-theme', theme);
    });
</script>

<svelte:head>
    <link rel="icon" href="/favicon.svg" />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
    <link href="https://fonts.googleapis.com/css2?family=Georama:ital,wght@0,100..900;1,100..900&family=Merriweather:ital,opsz,wght@0,18..144,300..900;1,18..144,300..900&family=Montserrat:ital,wght@0,100..900;1,100..900&family=Orbitron:wght@400..900&display=swap" rel="stylesheet">
</svelte:head>

<header class="topbar" data-theme={theme}>
    <a class="topbar-brand" href="/">VAR</a>
    <nav class="topbar-actions" aria-label="Primary navigation">
        <button
            class="topbar-theme-toggle"
            type="button"
            onclick={toggleTheme}
            aria-label="Toggle dark and light theme"
            data-theme-toggle
        >
            {#if theme === 'dark'}
                <img class="icon-moon" src="https://www.figma.com/api/mcp/asset/3dd0eb73-77cf-4645-ae0c-499bbe024b40" alt="" aria-hidden="true" />
            {:else}
                <svg class="icon-sun" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                    <circle cx="12" cy="12" r="4" stroke="currentColor" stroke-width="2" />
                    <path d="M12 2V5" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M12 19V22" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M2 12H5" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M19 12H22" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M4.93 4.93L7.05 7.05" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M16.95 16.95L19.07 19.07" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M4.93 19.07L7.05 16.95" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                    <path d="M16.95 7.05L19.07 4.93" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                </svg>
            {/if}
        </button>
        <a href="/#reviews">Recensioni</a>
        <a href="/#about">About</a>
    </nav>
</header>

<main>
    {@render children()}
</main>

<style>
    .topbar {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 24px;
        padding: 16px 48px;
        background: var(--color-topbar-bg, linear-gradient(90deg, #48acdc 20%, #d68176 50%, #f5d547 80%));
    }

    .topbar-brand,
    .topbar-actions a {
        color: var(--color-content-primary);
        text-decoration: none;
        font-family: var(--font-primary);
        font-size: 32px;
        font-weight: var(--font-weight-regular);
        line-height: 1;
    }

    .topbar-actions {
        display: flex;
        align-items: center;
        justify-content: flex-end;
        gap: 20px;
    }

    .topbar-theme-toggle {
        width: 29px;
        height: 29px;
        border: none;
        background: transparent;
        padding: 0;
        display: grid;
        place-items: center;
        cursor: pointer;
        color: var(--color-content-primary);
    }

    .topbar-theme-toggle .icon-moon,
    .topbar-theme-toggle .icon-sun {
        width: 21px;
        height: 21px;
        display: block;
    }

    :global(html[data-theme='dark']) .topbar-theme-toggle .icon-sun {
        display: none;
    }

    :global(html[data-theme='light']) .topbar-theme-toggle .icon-moon {
        display: none;
    }

    .topbar-theme-toggle .icon-moon {
        filter: brightness(0) invert(1);
    }

    .topbar-theme-toggle:focus-visible,
    .topbar-actions a:focus-visible,
    .topbar-brand:focus-visible {
        outline: 2px solid var(--color-content-primary);
        outline-offset: 4px;
        border-radius: 4px;
    }

    @media (max-width: 920px) {
        .topbar {
            padding: 14px 18px;
            gap: 12px;
        }

        .topbar-brand,
        .topbar-actions a {
            font-size: clamp(22px, 5.2vw, 32px);
        }

        .topbar-actions {
            gap: 12px;
        }

        .topbar-theme-toggle {
            width: 24px;
            height: 24px;
        }

        .topbar-theme-toggle .icon-moon,
        .topbar-theme-toggle .icon-sun {
            width: 18px;
            height: 18px;
        }
    }
</style>