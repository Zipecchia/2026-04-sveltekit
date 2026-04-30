<script lang="ts">
  // @ts-nocheck
  import CategorySelector from '$lib/components/CategorySelector.svelte';

  type Highlight = {
    label: string;
    location: string;
    address: string;
    city: string;
    image: string;
    border: string;
    badgeLabel: string;
  };

  type ArenaCard = {
    label: string;
    description: string;
    image: string;
    border: string;
  };

  const images = {
    palakennedy: 'https://www.figma.com/api/mcp/asset/44db144f-1380-4e13-8127-65d5ce651e04',
    palazElementari: 'https://www.figma.com/api/mcp/asset/71b1e4d5-2cde-41b8-b528-319a1e95d7da',
    barEnjoy: 'https://www.figma.com/api/mcp/asset/c580d11f-c56a-4f0e-8661-83732d966a55',
    mapPin: 'https://www.figma.com/api/mcp/asset/c2cb73e8-08f5-4bec-bddf-cb9d57bb131e',
    footerLogo: 'https://www.figma.com/api/mcp/asset/c0e3c02a-a6f9-4e47-bd34-16485b13e0cb'
  };

  const highlights: Highlight[] = [
    {
      label: 'PALA KENNEDY',
      location: 'Diavoli Rosa Brugherio',
      address: 'Via John e Robert Kennedy 15',
      city: 'Brugherio (MB)',
      image: images.palakennedy,
      border: '#48acdc',
      badgeLabel: 'Miglior campo'
    },
    {
      label: 'PALAZ. ELEMENTARI',
      location: 'A.S.D. Pallavolo Cassina',
      address: 'Via Trento',
      city: 'Cassina de Pecchi (MI)',
      image: images.palazElementari,
      border: '#d68176',
      badgeLabel: 'Migliori spogliatoi'
    },
    {
      label: 'BAR ENJOY',
      location: 'A.S.D. Pallavolo Cernusco',
      address: 'Via Michelangelo Buonarroti',
      city: 'Cernusco sul Naviglio (MI)',
      image: images.barEnjoy,
      border: '#f5d547',
      badgeLabel: 'Migliori servizi'
    }
  ];

  const bestArenaCards: ArenaCard[] = [
    {
      label: 'PALA KENNEDY',
      description: "Il campo da pallavolo di questa palestra è davvero eccezionale! La superficie è impeccabile e garantisce un gioco fluido e sicuro, mentre l'illuminazione è perfetta e permette di seguire ogni azione senza difficoltà. L'atmosfera è coinvolgente e motivante, ideale per dare sempre il massimo.",
      image: images.palakennedy,
      border: '#48acdc'
    },
    {
      label: 'PALAZ. ELEMENTARI',
      description: "Gli spogliatoi di questa palestra sono un vero sogno! La pulizia è impeccabile e si nota subito l'attenzione ai dettagli, mentre gli arredi moderni rendono l'ambiente accogliente e piacevole. Il comfort è davvero al top: spazi ben organizzati, tutto funzionale e curato.",
      image: images.palazElementari,
      border: '#d68176'
    },
    {
      label: 'BAR ENJOY',
      description: "Il bar di questa palestra è davvero eccezionale! Dalle centrifughe fresche e personalizzate agli snack salutari perfetti per il post-allenamento, c'è sempre qualcosa di gustoso e adatto a ogni esigenza. Ma non è solo il bar a fare la differenza: l'intera struttura offre servizi di alto livello.",
      image: images.barEnjoy,
      border: '#f5d547'
    }
  ];
</script>

<section class="page-home">
  <!-- HERO -->
  <div class="hero-shell">
    <div class="hero-copy">
      <h1>Venue<br />Advanced<br />Radar</h1>
      <div class="hero-tagline">Trova. Valuta. Gioca.</div>
      <p>Tutte le strutture sportive della Lombardia a portata di mano. Recensioni reali su campi da gioco, spogliatoi e servizi per chi non si accontenta di un posto qualunque.</p>
    </div>
  </div>

  <CategorySelector />

  <!-- SEZIONE HIGHLIGHTS (Le card bianche in alto) -->
  <section class="highlights-section" id="reviews">
    <div class="section-header">
      <h2>I migliori del 2025</h2>
      <p>Scopri chi si è classificato al top in ogni categoria durante l’ultimo anno</p>
    </div>

    <div class="highlight-grid">
      {#each highlights as highlight}
        <article class="highlight-card" style="border-color: {highlight.border}">
          <div class="featured-ribbon">
            <div class="featured-year" style="background-color: {highlight.border}">2025</div>
            <div class="featured-ribbon-label" style="background-color: {highlight.border}">{highlight.badgeLabel}</div>
          </div>

          <div class="highlight-media">
            <img src={highlight.image} alt={highlight.label} />
          </div>

          <div class="highlight-body">
            <h3 class="highlight-title">{highlight.label}</h3>
            <div class="highlight-details">
              <img class="icon-pin" src={images.mapPin} alt="Posizione" />
              <div class="address-text">
                <p><strong>{highlight.location}</strong></p>
                <p>{highlight.address}</p>
                <p>{highlight.city}</p>
              </div>
            </div>
          </div>
        </article>
      {/each}
    </div>
    <a class="link-arrow" href="#reviews">Vedi di più <span>→</span></a>
  </section>

  <!-- SEZIONE ARENA (Le card nere in basso) -->
  <section class="arena-section" id="about">
    <div class="gradient-overlay top"></div>
    <div class="gradient-overlay bottom"></div>

    <div class="section-header centered">
      <p class="overline">La migliore struttura del 2025</p>
      <h2>OPIQUAD ARENA</h2>
      <p>Pro Victoria Pallavolo<br />Viale G. Battista Stucchi - Monza</p>
    </div>

    <div class="arena-grid">
      {#each bestArenaCards as card}
        <article class="arena-card" style="border-color: {card.border};">
          <div class="arena-media">
            <img src={card.image} alt={card.label} />
          </div>
          <div class="arena-body">
            <div class="rating-stars" style="color: {card.border};">
              ★★★★★
            </div>
            <p>{card.description}</p>
          </div>
        </article>
      {/each}
    </div>

    <a class="link-arrow" href="#about">Vedi di più <span>→</span></a>
  </section>

  <footer class="page-footer">
    <img src={images.footerLogo} alt="Politecnico Milano" />
  </footer>
</section>

<style>
  /* RESET & BASE */
  .page-home {
    min-height: 100vh;
    font-family: var(--font-primary);
    background: linear-gradient(89deg, #6591d5 0.35%, #d68176 53.84%, #f5d547 101.68%);
  }

  .section-header {
    text-align: center;
    margin-bottom: 48px;
    color: white;
  }
  .section-header h2 { font-size: 50px; margin: 0; }
  .section-header p { font-size: 26px; opacity: 0.9; }

  /* HERO */
  .hero-shell {
    padding: 72px 24px;
    text-align: center;
    position: relative;
    background: linear-gradient(180deg, transparent 0%, #070707 100%);
  }
  .hero-copy h1 { font-size: clamp(4rem, 8vw, 6.5rem); line-height: 0.9; margin: 0; color: white; }
  .hero-tagline { font-size: 48px; font-weight: 600; color: white; margin-top: 10px; }
  .hero-copy p { font-size: 28px; max-width: 800px; margin: 20px auto; color: white; }

  /* --- STILE 1: HIGHLIGHT CARDS (BIANCHE) --- */
  .highlights-section { background-color: #000; padding: 80px 24px; }
  
  .highlight-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, 370px);
    justify-content: center;
    gap: 40px;
  }

  .highlight-card {
    background: #ffffff; /* Sfondo Bianco */
    border: 4px solid;
    border-radius: 24px;
    position: relative;
    overflow: hidden;
    color: #070707; /* Testo Nero */
  }

  .highlight-media img {
    width: 100%;
    aspect-ratio: 16/10;
    object-fit: cover;
    display: block;
  }

  .highlight-body { padding: 24px; }
  .highlight-title { font-size: 30px; font-weight: 700; margin: 0 0 12px 0; text-transform: uppercase; }
  .highlight-details { display: flex; gap: 12px; align-items: flex-start; }
  .highlight-details p { margin: 0; font-size: 16px; line-height: 1.3; }
  .icon-pin { width: 20px; margin-top: 4px; }

  /* Ribbon per Highlights */
  .featured-ribbon { position: absolute; top: -10px; left: 10px; display: flex; align-items: center; z-index: 5; }
  .featured-year { width: 45px; height: 45px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: bold; color: white; font-size: 14px; }
  .featured-ribbon-label { padding: 4px 12px; font-size: 12px; font-weight: bold; color: white; clip-path: polygon(0 0, 90% 0, 100% 50%, 90% 100%, 0 100%); margin-left: -5px; }

  /* --- STILE 2: ARENA CARDS (NERE) --- */
  .arena-section {
    padding: 100px 24px;
    background: linear-gradient(180deg, #000 0%, #48acdc 20%, #d68176 50%, #f5d547 80%, #000 100%);
    position: relative;
  }

  .arena-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, 370px);
    justify-content: center;
    gap: 40px;
    position: relative; z-index: 2;
  }

  .arena-card {
    background: #070707; /* Sfondo Nero */
    border: 2px solid;
    border-radius: 28px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    min-height: 520px;
  }

  .arena-media { padding: 14px 14px 0 14px; }
  .arena-media img { width: 100%; aspect-ratio: 16/10; object-fit: cover; border-radius: 20px; }

  .arena-body { padding: 24px; color: white; text-align: left; }
  .rating-stars { font-size: 32px; text-align: center; margin-bottom: 12px; }
  .arena-body p { font-size: 18px; line-height: 1.5; margin: 0; }

  /* OVERLAYS & UTILS */
  .gradient-overlay { position: absolute; left: 0; right: 0; height: 150px; z-index: 1; pointer-events: none; }
  .gradient-overlay.top { top: 0; background: linear-gradient(to bottom, #000, transparent); }
  .gradient-overlay.bottom { bottom: 0; background: linear-gradient(to top, #000, transparent); }

  .centered .overline { font-size: 22px; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 5px; }
  .centered h2 { font-size: 60px; }

  .link-arrow {
    display: block; width: fit-content; margin: 40px auto 0;
    color: white; font-size: 28px; text-decoration: none; font-weight: 500;
    position: relative; z-index: 2;
  }

  .page-footer { padding: 60px; background: #000; text-align: center; }
  .page-footer img { height: 45px; }

  @media (max-width: 1150px) {
    .highlight-grid, .arena-grid { grid-template-columns: 1fr; max-width: 370px; margin: 0 auto; }
  }
</style>