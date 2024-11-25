<script>
	import Stats2 from './stats2.svelte';
    // @ts-ignore
    import Hero from './hero.svelte';
</script>

<style>
    .container {
        display: flex;
        justify-content: center; /* Center the components horizontally */
        align-items: flex-start; /* Align components at the top */
        gap: 2rem; /* Add spacing between the components */
        padding: 2rem;
    }

    .stats {
        flex: 1; /* Allows Stats to take up equal space */
    }

    .hero {
        flex: 1; /* Allows Hero to take up equal space */
    }

    @media (max-width: 768px) {
        .container {
            flex-direction: column; /* Stack components vertically on smaller screens */
            align-items: center; /* Center align when stacked */
        }

        .stats, .hero {
            flex: unset;
            width: 100%; /* Take full width on smaller screens */
        }
    }
</style>

<div class="container">
   <div class="hero">
        <Hero />
    </div>
    <div class="stats">
        <Stats2 />
    </div>
</div>
