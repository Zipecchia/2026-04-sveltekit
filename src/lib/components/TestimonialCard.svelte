<script lang="ts">
  // @ts-nocheck
  let {
    imageSrc = '',
    rating = 5,
    variant = 'yellow',
    children
  } = $props<{ imageSrc?: string; rating?: number; variant?: 'yellow' | 'red'; children?: unknown }>();

  const starSrc = '/star.svg';
</script>

<div class="testimonial-card" class:red={variant === 'red'}>
  <div class="image-container">
    {#if imageSrc}
      <img class="testimonial-image" src={imageSrc} alt="Testimonial screenshot" />
    {/if}
  </div>

  <div class="stars-container">
    {#each Array(rating) as _}
      <div class="star">
        {#if starSrc}
          <img src={starSrc} alt="Star" />
        {/if}
      </div>
    {/each}
  </div>

  <div class="text-container">
    <div class="text-content">
      <div class="testimonial-text">
        {#if children}
          {@render children()}
        {/if}
      </div>
    </div>
  </div>
</div>

<style>
  .testimonial-card {
    background-color: var(--color-background-primary);
    border: var(--border-width-thin) solid var(--third-yellow-500);
    border-radius: var(--border-radius-md);
    width: 336px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  /* Se la variante è red, sovrascrivi il colore del bordo */
  .testimonial-card.red {
    border-color: var(--secondary-red-400);
  }

  .image-container {
    width: 100%;
    padding: var(--spacing-2);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .testimonial-image {
    width: 100%;
    aspect-ratio: var(--aspect-ratio-testimonial-image);
    border-radius: var(--border-radius-sm);
    object-fit: cover;
  }

  .stars-container {
    width: 100%;
    display: flex;
    gap: 7px;
    align-items: center;
    justify-content: center;
    padding: var(--spacing-2) var(--spacing-0);
  }

  .star {
    width: 38.382px;
    height: 36.135px;
    position: relative;
  }

  .star img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  .text-container {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: var(--spacing-2) 0 var(--spacing-6) 0;
  }

  .text-content {
    padding: 0 var(--spacing-3);
    width: 100%;
  }

  .testimonial-text {
    font-family: var(--font-primary);
    font-size: var(--font-size-xs);
    font-weight: var(--font-weight-regular);
    line-height: var(--line-height-normal);
    letter-spacing: var(--letter-spacing-normal);
    color: var(--color-content-primary);
    margin: 0;
    font-variation-settings: var(--font-variation-width);
  }
</style>