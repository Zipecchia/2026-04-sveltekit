<script lang="ts">
  import TestimonialCard from '$lib/components/TestimonialCard.svelte';

  // Definiamo l'interfaccia per il contenuto del modulo markdown
  interface TestimonialModule {
    default: any;
    metadata: {
      title?: string;
      rating?: number;
      variant?: "yellow" | "blue" | "green"; // o i valori che usi
      imageSrc?: string;
    };
  }

  // Import all testimonial markdown files
  const testimonialModules = import.meta.glob('./content/testimonials/*.md', {
    eager: true
  });

  // Process the imported modules
  const testimonials = Object.entries(testimonialModules).map(([path, module]) => {
    // Cast del modulo all'interfaccia definita sopra
    const { default: component, metadata } = module as TestimonialModule;

    return {
      title: metadata?.title || 'Testimonial',
      rating: metadata?.rating || 5,
      variant: metadata?.variant || 'yellow',
      imageSrc: metadata?.imageSrc || '',
      component,
      metadata
    };
  });
</script>

<style>
  .testimonials-grid {
    display: flex;
    gap: 2rem;
    flex-wrap: wrap;
    justify-content: center;
    padding: 2rem;
    min-height: 100vh;
    background-color: var(--color-background-primary);
  }

  h1 {
    text-align: center;
    color: var(--color-content-primary);
    font-family: var(--font-primary);
    font-size: var(--font-size-lg);
    font-weight: var(--font-weight-semibold);
    margin-bottom: 2rem;
    font-variation-settings: var(--font-variation-width);
  }
</style>

<h1>Testimonial Cards</h1>

<div class="testimonials-grid">
  {#each testimonials as testimonial}
    <TestimonialCard
      imageSrc={testimonial.imageSrc}
      rating={testimonial.rating}
      variant={testimonial.variant}
    >
      <svelte:component this={testimonial.component} />
    </TestimonialCard>
  {/each}
</div>