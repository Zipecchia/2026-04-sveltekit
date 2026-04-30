<script lang="ts">
  // @ts-nocheck
  type Category = {
    id: string;
    label: string;
    color: string;
    description: string;
    ctaText: string;
    imageSrc: string;
  };

  let {
    categories = [
    {
      id: 'campi',
      label: 'CAMPI DA GIOCO',
      color: '#48acdc',
      description: 'In questa sezione trovi i feedback sulle superfici, l\'illuminazione e la manutenzione dei campi da gioco. Scopri se il pavimento è troppo scivoloso o se le luci sono fastidiose!',
      ctaText: 'Tutti i campi da gioco',
      imageSrc: 'https://www.figma.com/api/mcp/asset/42fec47b-1356-40cb-9d8f-f0c09bab8e50'
    },
    {
      id: 'spogliatoi',
      label: 'SPOGLIATOI',
      color: '#d68176',
      description: 'Scopri le condizioni degli spogliatoi: pulizia, comfort, servizi igienici e qualità delle strutture dedicate al riposo e al cambio.',
      ctaText: 'Tutti gli spogliatoi',
      imageSrc: 'https://www.figma.com/api/mcp/asset/159daafb-28f2-46f3-8a9b-7404df09ff2b'
    },
    {
      id: 'servizi',
      label: 'SERVIZI',
      color: '#f5d547',
      description: 'Valuta i servizi aggiuntivi: bar, parcheggio, reception, assistenza medica e tutti i servizi complementari offerti dalla struttura.',
      ctaText: 'Tutti i servizi',
      imageSrc: 'https://www.figma.com/api/mcp/asset/b3d09066-fb8a-406a-9ad3-1495b1f225f3'
    },
    {
      id: 'overall',
      label: 'OVERALL',
      color: '#f5d547',
      description: 'La valutazione complessiva della struttura: qualità generale, rapporto qualità-prezzo, soddisfazione globale e raccomandazioni.',
      ctaText: 'Valutazioni complessive',
      imageSrc: 'https://www.figma.com/api/mcp/asset/f6aa1553-8abb-4c5b-abac-e98f777153d7'
    }
    ]
  } = $props<{ categories?: Category[] }>();

  let selectedCategory = $state<string | null>('campi');

  function selectCategory(categoryId: string) {
    selectedCategory = categoryId;
  }

  let selectedCategoryData = $derived(
    selectedCategory
      ? categories.find((cat) => cat.id === selectedCategory) ?? categories[0]
      : categories[0]
  );

  let serviceDetailGradient = $derived.by(() => {
    switch(selectedCategory) {
      case 'campi':
        return 'linear-gradient(180deg, rgb(72, 172, 220) 7.6923%, rgba(72, 172, 220, 0) 100%), linear-gradient(90deg, var(--color-background-primary) 0% 100%)';
      case 'spogliatoi':
        return 'linear-gradient(180deg, rgb(214, 129, 118) 7.6923%, rgba(214, 129, 118, 0) 100%), linear-gradient(90deg, var(--color-background-primary) 0% 100%)';
      case 'servizi':
        return 'linear-gradient(180deg, rgb(245, 213, 71) 7.6923%, rgba(245, 213, 71, 0) 100%), linear-gradient(90deg, var(--color-background-primary) 0% 100%)';
      case 'overall':
        return 'linear-gradient(0deg, var(--color-background-primary) 20%, transparent 100%), linear-gradient(270deg, rgb(245, 213, 71) 0%, rgb(214, 129, 118) 50%, rgb(72, 172, 220) 100%)';
      default:
        return 'linear-gradient(180deg, rgb(72, 172, 220) 7.6923%, rgba(72, 172, 220, 0) 100%), linear-gradient(90deg, var(--color-background-primary) 0% 100%)';
    }
  });
</script>

<section class="category-selector">
  <!-- Top Row: Service Buttons -->
  <div class="service-buttons">
    {#each categories as category}
      <button
        class="service-button {selectedCategory === category.id ? 'active' : ''} {category.id === 'overall' && selectedCategory === category.id ? 'gradient-border' : ''}"
        style:border-color={category.id === 'overall' && selectedCategory === category.id ? 'transparent' : (selectedCategory === category.id ? category.color : '#dbdbdb')}
        onclick={() => selectCategory(category.id)}
        aria-label={category.label}
      >
        <img src={category.imageSrc} alt={category.label} />
      </button>
    {/each}
  </div>

  <!-- Bottom Row: Selected Service Detail -->
  {#if selectedCategoryData}
    <div class="service-detail" style="background-image: {serviceDetailGradient}">
      <div class="service-content">
        <div class="service-text">
          <h3 class="service-title">{selectedCategoryData.label}</h3>
          <p class="service-description">{selectedCategoryData.description}</p>
          <a href={'#' + selectedCategoryData.id} class="service-cta">
            <span>{selectedCategoryData.ctaText}</span>
            <span class="arrow-icon">→</span>
          </a>
        </div>
        <div class="service-visual">
          <img src={selectedCategoryData.imageSrc} alt={selectedCategoryData.label} />
        </div>
      </div>
    </div>
  {/if}
</section>

<style>
  .category-selector {
    width: 100%;
    background: #070707;
    display: flex;
    flex-direction: column;
  }

  /* Service Buttons */
  .service-buttons {
    display: flex;
    gap: 23px;
    justify-content: center;
    align-items: center;
    padding: 20px 160px 32px;
    background: var(--color-background-primary);
  }

  .service-button {
    width: auto;
    height: 130px;
    border: 3.94px solid #dbdbdb;
    border-radius: 984.055px;
    background: var(--color-background-primarys);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0px 60px;
    box-sizing: border-box;
    transition: all 0.3s ease;
    overflow: hidden;
    position: relative;
  }

  .service-button::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: inherit;
    background: var(--color-background-primary);
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .service-button:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 25px rgba(72, 172, 220, 0.3);
    border-color: rgba(72, 172, 220, 0.7);
  }

  .service-button:hover::before {
    opacity: 1;
  }

  .service-button.active {
    box-shadow: 0 0 20px rgba(72, 172, 220, 0.24);
  }

  .service-button.active:hover {
    box-shadow: 0 8px 30px rgba(72, 172, 220, 0.32);
  }

  .service-button.gradient-border {
    background: linear-gradient(var(--color-background-primary)) padding-box,
                linear-gradient(90deg, #f5d547 0%, #d68176 50%, #48acdc 100%) border-box;
    border: 3.94px solid transparent;
    box-shadow: 0 0 20px rgba(245, 213, 71, 0.24);
  }

  .service-button.gradient-border:hover {
    box-shadow: 0 8px 30px rgba(245, 213, 71, 0.32);
  }

  .service-button img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    object-position: center;
    border-radius: 20px;
    transition: transform 0.3s ease;
    position: relative;
    z-index: 1;
  }

  .service-button:hover img {
    transform: scale(1.04);
  }

  /* Service Detail */
  .service-detail {
    padding: 72px 168px;
    transition: all 0.5s ease;
    background-size: cover;
    background-position: center;
  }

  .service-content {
    display: flex;
    gap: 23px;
    align-items: flex-start;
    max-width: 1512px;
    margin: 0 auto;
    animation: fadeIn 0.5s ease forwards;
  }

  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .service-text {
    flex: 0 0 577px;
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  .service-title {
    font-family: 'Georama', sans-serif;
    font-weight: 600;
    font-size: 64px;
    line-height: 1;
    color: #fafafa;
    margin: 0;
    width: 490px;
  }

  .service-description {
    font-family: 'Georama', sans-serif;
    font-weight: 400;
    font-size: 30px;
    line-height: 1;
    color: #000000;
    margin: 0;
    width: 576px;
  }

  .service-cta {
    display: flex;
    align-items: center;
    gap: 16px;
    font-family: 'Georama', sans-serif;
    font-weight: 400;
    font-size: 32px;
    color: white;
    text-decoration: none;
    width: auto;
  }

  .service-cta .arrow-icon {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    flex-shrink: 0;
    transition: transform 0.3s ease;
  }

  .service-cta:hover .arrow-icon {
    transform: translateX(8px);
  }

  .service-visual {
    width: 576px;
    height: 433.231px;
    position: relative;
    overflow: hidden;
    border-radius: 16px;
  }

  .service-visual img {
    width: 109.12%;
    height: 144.98%;
    position: absolute;
    left: -4.56%;
    top: -22.11%;
    object-fit: cover;
  }

  /* Responsive */
  @media (max-width: 1024px) {
    .service-buttons {
      padding: 20px 24px 32px;
      gap: 16px;
    }

    .service-button {
      width: 120px;
      height: 92px;
      padding: 8px 40px;
    }

    .service-detail {
      padding: 48px 24px;
    }

    .service-content {
      flex-direction: column;
      gap: 32px;
    }

    .service-text {
      flex: none;
    }

    .service-title {
      font-size: 48px;
      width: 100%;
    }

    .service-description {
      font-size: 24px;
      width: 100%;
    }

    .service-cta {
      font-size: 24px;
      width: auto;
    }

    .service-visual {
      width: 100%;
      height: 300px;
    }
  }

  @media (max-width: 768px) {
    .service-buttons {
      flex-wrap: wrap;
      gap: 12px;
    }

    .service-button {
      width: 100px;
      height: 76px;
      padding: 6px 32px;
    }

    .service-detail {
      padding: 32px 16px;
    }

    .service-title {
      font-size: 36px;
    }

    .service-description {
      font-size: 20px;
    }

    .service-cta {
      font-size: 20px;
    }

    .service-visual {
      height: 250px;
    }
  }
</style>