<script lang="ts">
  // @ts-nocheck
  import CategorySelector from '$lib/components/CategorySelector.svelte';

  type Highlight = {
    label: string;
    location: string;
    address: string;
    city: string;
    image: string;
    hoverImage?: string;
    border: string;
    description: string;
    badgeLabel: string;
  };

  type ArenaCard = {
    label: string;
    description: string;
    image: string;
    border: string;
  };

  const images = {
    service1: 'https://www.figma.com/api/mcp/asset/0fc33faf-cb40-45e4-bd88-d18fab6f2cae',
    service2: 'https://www.figma.com/api/mcp/asset/70a82ba8-996a-4caa-84d9-aef0ebeb13ca',
    service3: 'https://www.figma.com/api/mcp/asset/853bcb75-7dea-4055-80a8-9ddab3560f83',
    service4: 'https://www.figma.com/api/mcp/asset/e1e9a440-0bc8-44ae-9c2d-c3cde4f00b09',
    campo: 'https://www.figma.com/api/mcp/asset/9453ad7c-046d-4642-b1cc-71fae56bc0e2',
    spogliatoi: 'https://www.figma.com/api/mcp/asset/6fcdbe25-60b2-4d54-a1a7-e97cff6e9949',
    palaz: 'https://www.figma.com/api/mcp/asset/07d6e788-df49-4681-9498-0f9faf96c557',
    bar: 'https://www.figma.com/api/mcp/asset/c4a49cd5-7f13-4ea5-8c02-e425e4a2e0f8',
    palakennedy: 'https://www.figma.com/api/mcp/asset/44db144f-1380-4e13-8127-65d5ce651e04',
    palazElementari: 'https://www.figma.com/api/mcp/asset/71b1e4d5-2cde-41b8-b528-319a1e95d7da',
    barEnjoy: 'https://www.figma.com/api/mcp/asset/c580d11f-c56a-4f0e-8661-83732d966a55',
    arrow: 'https://www.figma.com/api/mcp/asset/33f93031-4e04-45ce-ab34-2980483413c1',
    moon: 'https://www.figma.com/api/mcp/asset/0719ac73-14ee-45c0-9449-c0258fd9a21b',
    mapPin: 'https://www.figma.com/api/mcp/asset/c2cb73e8-08f5-4bec-bddf-cb9d57bb131e',
    footerLogo: 'https://www.figma.com/api/mcp/asset/c0e3c02a-a6f9-4e47-bd34-16485b13e0cb'
  };

  const services = [
    { id: 'campi', label: 'Campi da gioco', image: images.service1, active: true },
    { id: 'spogliatoi', label: 'Spogliatoi', image: images.service2 },
    { id: 'servizi', label: 'Servizi', image: images.service3 },
    { id: 'overall', label: 'Overall', image: images.service4 }
  ];

  const highlights: Highlight[] = [
    {
      label: 'PALA KENNEDY',
      location: 'Diavoli Rosa Brugherio',
      address: 'Via John e Robert Kennedy 15',
      city: 'Brugherio (MB)',
      image: images.palakennedy,
      border: '#48acdc',
      badgeLabel: 'Miglior campo',
      description: 'Il campo da pallavolo di questa palestra è eccezionale! Superficie impeccabile, illuminazione perfetta e un\'atmosfera che sprona a dare il massimo.'
    },
    {
      label: 'PALAZ. ELEMENTARI',
      location: 'A.S.D. Pallavolo Cassina',
      address: 'Via Trento',
      city: 'Cassina de Pecchi (MI)',
      image: images.palazElementari,
      border: '#d68176',
      badgeLabel: 'Migliori spogliatoi',
      description: 'Gli spogliatoi di questa palestra sono un sogno! Pulizia impeccabile, arredi moderni e comfort insuperabile, scordatevi le docce fredde, questo si che è lusso!'
    },
    {
      label: 'BAR ENJOY',
      location: 'A.S.D. Pallavolo Cernusco',
      address: 'Via Michelangelo Buonarroti',
      city: 'Cernusco sul Naviglio (MI)',
      image: images.barEnjoy,
      border: '#f5d547',
      badgeLabel: 'Migliori servizi',
      description: 'Il bar di questa palestra è eccezionale! Dalle bevande fresche agli snack salutari, c\'è sempre qualcosa di buono per ricaricarsi.'
    }
  ];

  const bestArenaCards: ArenaCard[] = [
    {
      label: 'PALA KENNEDY',
      description: "Il campo da pallavolo di questa palestra è davvero eccezionale! Superficie impeccabile, illuminazione perfetta e un’atmosfera coinvolgente.",
      image: images.palakennedy,
      border: '#48acdc'
    },
    {
      label: 'PALAZ. ELEMENTARI',
      description: 'Gli spogliatoi di questa palestra sono un vero sogno! Pulizia impeccabile, arredi moderni e comfort insuperabile.',
      image: images.palazElementari,
      border: '#d68176'
    },
    {
      label: 'BAR ENJOY',
      description: 'Il bar di questa palestra è eccezionale! Dalle centrifughe fresche agli snack salutari c’è sempre qualcosa per tutti.',
      image: images.barEnjoy,
      border: '#f5d547'
    }
  ];
</script>

<section class="page-home">
  <div class="hero-shell">
    <div class="hero-copy">
      <h1>Venue<br />Advanced<br />Radar</h1>
      <div class="hero-tagline">Trova. Valuta. Gioca.</div>
      <p>Tutte le strutture sportive della Lombardia a portata di mano. Recensioni reali su campi da gioco, spogliatoi e servizi per chi non si accontenta di un posto qualunque.</p>
    </div>
  </div>

  <CategorySelector />

  <section class="highlights" id="reviews" style="background-color:black;">
     <div class="section-header">
    </div>
    <div class="section-header">
      <h2>I migliori del 2025</h2>
      <p>Scopri chi si è classificato al top in ogni categoria durante l’ultimo anno</p>
    </div>

    <div class="highlight-grid">
  {#each highlights as highlight}
    <div class="card-column">
      <!-- TOP SOLID CARD -->
      <article class="highlight-card" style="background-color: {highlight.border}; border-color: {highlight.border}">
        <div class="featured-ribbon">
          <div class="featured-year" style="background-color: {highlight.border}">2025</div>
          <div class="featured-ribbon-label" style="background-color: {highlight.border}">{highlight.badgeLabel}</div>
        </div>

        <div class="featured-media">
          <img class="highlight-card-image" src={highlight.image} alt={highlight.label} />
        </div>

        <div class="highlight-card-body">
          <h2 class="card-title-main">{highlight.label}</h2>
          <div class="location-row">
            <img class="icon-pin" src={images.mapPin} alt="Posizione" />
            <div class="address-text">
              <p><strong>{highlight.location}</strong></p>
              <p>{highlight.address}</p>
              <p>{highlight.city}</p>
            </div>
          </div>
        </div>
      </article>

      <!-- BOTTOM OUTLINED BOX -->
      <div class="description-box-bottom" style="border-color: {highlight.border}">
        <p>{highlight.description}</p>
      </div>
    </div>
  {/each}
</div>
  </section>
    <a class="link-arrow view-more"href="#reviews"style="display:block; width:fit-content; margin:5 auto;">Vedi di più<span class="arrow-icon">→</span></a>
 <section
  class="best-arena"
  id="about"
  style="background: linear-gradient(
    linear,
    #000000 0%,
    #48acdc 20%,
    #d68176 50%,
    #f5d547 80%,
    #000000 100%
  ); position: relative;"
>

  <div style="
    position:absolute;
    top:0;
    left:0;
    right:0;
    height:120px;
    background: linear-gradient(to bottom, rgba(0,0,0,1), rgba(0,0,0,0));
    pointer-events:none;
  "></div>

  <div style="
    position:absolute;
    bottom:0;
    left:0;
    right:0;
    height:120px;
    background: linear-gradient(to top, rgba(0,0,0,1), rgba(0,0,0,0));
    pointer-events:none;
  "></div>

  <div class="section-header centered">

 
      <p class="overline">La migliore struttura del 2025</p>
      <h2>OPIQUAD ARENA</h2>
      <p>Pro Victoria Pallavolo<br />Viale G. Battista Stucchi - Monza</p>
    </div>

    <div class="arena-grid">
      {#each bestArenaCards as card}
        <article class="arena-card" style="border-color: {card.border}">
          <img class="arena-card-image" src={card.image} alt={card.label} />
          <div class="arena-card-body">
            <div class="arena-card-title">{card.label}</div>
            <p>{card.description}</p>
          </div>
        </article>
      {/each}
    </div>

  <a class="link-arrow view-more"href="#about"style="display:block; width:fit-content; margin:5 auto;">Vedi di più<span class="arrow-icon">→</span></a>
  </section>

  <footer class="page-footer">
    <img src={images.footerLogo} alt="Politecnico Milano" />
  </footer>
</section>

<style>
  .page-home {
    min-height: 100vh;
    color: var(--color-content-primary);
    background: linear-gradient(89deg, #6591d5 0.35%, #d68176 53.84%, #f5d547 101.68%);
  }

  .hero-shell {
    max-width: 1512px;
    margin: 0 auto;
    padding: 72px 24px;
    position: relative;
  }

  .hero-shell::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(180deg, rgba(7, 7, 7, 0) 0%, rgba(7, 7, 7, 0.72) 62%, #070707 100%);
    pointer-events: none;
    z-index: 0;
  }

  .section-header,
  .arena-grid,
  .highlight-grid {
    position: relative;
    z-index: 1;
  }

  .hero-copy {
    position: relative;
    z-index: 1;
    max-width: 1080px;
    margin: 0 auto;
    text-align: center;
    padding: 0 24px;
  }

  .hero-copy h1 {
    font-family: var(--font-primary);
    font-weight: var(--font-weight-medium);
    font-size: clamp(4.5rem, 6vw, 6.5rem);
    line-height: 0.8;
    margin: 0;
    color: #ffffff;
  }

  .hero-tagline {
    margin-top: 1rem;
    font-family: var(--font-primary);
    font-weight: var(--font-weight-semibold);
    font-size: 50px;
    line-height: 1;
    color: #ffffff;
  }

  .hero-copy p {
    margin: 24px auto 0;
    max-width: 760px;
    font-size: 30px;
    line-height: 1.2;
    font-family: var(--font-primary);
    color: rgba(255, 255, 255, 0.98);
  }

  .highlights,
  .best-arena {
    padding: 88px 24px;
  }

  .section-header {
    display: grid;
    gap: 16px;
    max-width: 920px;
    margin: 0 auto 48px;
    text-align: center;
  }

  .section-header h2 {
    margin: 0;
    font-family: var(--font-primary);
    font-weight: var(--font-weight-semibold);
    font-size: 50px;
    line-height: 1;
  }

  .section-header p {
    margin: 0;
    font-size: 30px;
    line-height: 1.2;
  }

  .section-header.centered {
    margin-top: 24px;
  }

  .section-header.centered .overline {
    font-size: 26px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    opacity: 0.9;
    margin: 0;
  }

  .arena-grid,
  .highlight-grid {
    display: grid;
    grid-template-columns: repeat(3, 370px);
    justify-content: center;
    gap: 50px;
  }

  .highlight-card,
  .arena-card {
    border: 4px solid;
    border-radius: 20px;
    overflow: hidden;
    background: var(--color-background-primary);
    display: flex;
    flex-direction: column;
    min-height: 507px;
    position: relative;
    transition: all 0.3s ease;
  }

  .highlight-card--featured {
    overflow: hidden;
    width: 370px;
    height: 507px;
  }

  .featured-ribbon {
    position: absolute;
    left: 10px;
    top: -12px;
    z-index: 20;
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 0;
  }

  .featured-year {
    width: 58px;
    height: 58px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-primary);
    font-weight: var(--font-weight-semibold);
    font-size: 22px;
    color: rgba(255, 226, 145, 0.98);
    background: #58a9d4;
    box-shadow: 0 5px 0 rgba(0, 0, 0, 0.18);
    position: relative;
  }

  .featured-ribbon-label {
    height: 26px;
    display: flex;
    align-items: center;
    padding: 0 18px 0 14px;
    font-family: var(--font-primary);
    font-weight: var(--font-weight-semibold);
    font-size: 16px;
    color: #fafafa;
    background: #58a9d4;
    clip-path: polygon(0 0, calc(100% - 14px) 0, 100% 50%, calc(100% - 14px) 100%, 0 100%);
    margin-left: -4px;
  }

  .featured-media {
    padding: 10px 10px 0;
    background: #58a9d4;
    border-radius: 20px 20px 0 0;
  }

  .highlight-card-image--featured {
    margin: 0;
    border-radius: 14px 14px 0 0;
    aspect-ratio: 618 / 355;
  }

  .highlight-card-body--featured {
    padding-top: 10px;
    background: #58a9d4;
    gap: 8px;
  }

  .highlight-card-title--featured {
    color: #070707;
    font-size: 28px;
  }

  .highlight-card-details--featured p {
    color: #070707;
    line-height: 1.05;
  }

  .highlight-card:hover {
    transform: scale(1.02);
  }

  .highlight-card-image,
  .arena-card-image {
    width: 100%;
    aspect-ratio: 618 / 355;
    object-fit: cover;
    display: block;
  }

  .highlight-card-body,
  .arena-card-body {
    padding: 20px;
    display: grid;
    gap: 18px;
  }

  .highlight-card-title,
  .arena-card-title {
    font-family: var(--font-primary);
    font-weight: var(--font-weight-semibold);
    font-size: 30px;
    line-height: 1.1;
  }

  .highlight-card-details {
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }

  .highlight-card-details .icon-pin {
    width: 24px;
    height: 24px;
    flex-shrink: 0;
  }

  .arrow-icon {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    flex-shrink: 0;
    transition: transform 0.3s ease;
  }

  .arrow-icon {
    transform: translateX(8px);
  }

  .highlight-card-details p,
  .arena-card-body p {
    margin: 0;
    font-family: var(--font-primary);
    font-size: 20px;
    line-height: 1.4;
  }

  .highlight-card-description {
    position: absolute;
    bottom: 120px;
    left: 20px;
    right: 20px;
    border: 4px solid;
    border-radius: 16px;
    padding: 16px;
    background: #070707;
    opacity: 0;
    transition: opacity 0.3s ease;
    pointer-events: none;
    z-index: 10;
  }

  .highlight-card:hover .highlight-card-description {
    opacity: 1;
  }

  .highlight-card-description p {
    margin: 0;
    font-family: var(--font-primary);
    font-size: 18px;
    line-height: 1.4;
    color: white;
  }

  .arena-card-body {
    background: rgba(255, 255, 255, 0.04);
  }

  .view-more {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    margin: 42px auto 0;
    font-size: 32px;
    color: var(--color-content-primary);
    text-decoration: none;
    font-family: var(--font-primary);
  }

  .page-footer {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 32px 24px;
    background: linear-gradient(90deg, rgba(245, 213, 71, 0.35), rgba(214, 129, 118, 0.35), rgba(101, 145, 213, 0.35));
  }

  .page-footer img {
    height: 44px;
    object-fit: contain;
  }

  @media (max-width: 1120px) {
    .arena-grid,
    .highlight-grid {
      grid-template-columns: 1fr;
    }
  }

  @media (max-width: 720px) {
    .hero-copy h1 {
      font-size: 3.6rem;
    }

    .hero-tagline {
      font-size: 36px;
    }

    .hero-copy p,
    .section-header p,
    .highlight-card-details p,
    .arena-card-body p {
      font-size: 22px;
    }

    .hero-shell,
    .highlights,
    .best-arena,
    .page-footer {
      padding-left: 18px;
      padding-right: 18px;
    }
  }
</style>
