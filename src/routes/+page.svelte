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
    description: string;
  };

  type ArenaCard = {
    label: string;
    description: string;
    image: string;
    border: string;
  };

  const images = {
    palakennedy: '/campoBest.png',
    palazElementari: '/spogliatoiBest.png',
    barEnjoy: '/barBest.png',
    mapPin: 'https://www.figma.com/api/mcp/asset/c2cb73e8-08f5-4bec-bddf-cb9d57bb131e',
    footerLogo: 'https://www.figma.com/api/mcp/asset/c0e3c02a-a6f9-4e47-bd34-16485b13e0cb',
    campoArena: '/campoArena.png',
    barArena: '/barArena.png',
    spogliatoiArena: '/spogliatoiArena.png'
  };

  const highlights: Highlight[] = [
    {
      label: 'PALA KENNEDY',
      location: 'Diavoli Rosa Brugherio',
      address: 'Via John e Robert Kennedy 15',
      city: 'Brugherio (MB)',
      image: images.palakennedy,
      border: '#48acdc',
      badgeLabel: 'Miglior campo',
      description: 'Superficie professionale in taraflex e illuminazione LED di ultima generazione.'
    },
    {
      label: 'PALAZ. ELEMENTARI',
      location: 'A.S.D. Pallavolo Cassina',
      address: 'Via Trento',
      city: 'Cassina de Pecchi (MI)',
      image: images.palazElementari,
      border: '#d68176',
      badgeLabel: 'Migliori spogliatoi',
      description: 'Ampi spazi, docce moderne e pulizia impeccabile dopo ogni turno.'
    },
    {
      label: 'BAR ENJOY',
      location: 'A.S.D. Pallavolo Cernusco',
      address: 'Via Michelangelo Buonarroti',
      city: 'Cernusco sul Naviglio (MI)',
      image: images.barEnjoy,
      border: '#f5d547',
      badgeLabel: 'Migliori servizi',
      description: 'Area ristoro completa con vista sui campi e ottima selezione snack.'
    }
  ];

  const bestArenaCards: ArenaCard[] = [
    {
      label: 'BEST CAMPO',
      description: "Il campo da pallavolo di questa palestra è davvero eccezionale! La superficie è impeccabile e garantisce un gioco fluido e sicuro, mentre l’illuminazione è perfetta e permette di seguire ogni azione senza difficoltà. L’atmosfera è coinvolgente e motivante, ideale per dare sempre il massimo. Anche gli spazi attorno al campo sono ben curati, rendendo l’esperienza di gioco ancora più piacevole. Un ambiente davvero perfetto per chi ama questo sport!",
      image: images.campoArena,
      border: '#48acdc'
    },
    {
      label: 'BEST SPOGLIATOI',
      description: "Gli spogliatoi di questa palestra sono un vero sogno! La pulizia è impeccabile e si nota subito l’attenzione ai dettagli, mentre gli arredi moderni rendono l’ambiente accogliente e piacevole. Il comfort è davvero al top: spazi ben organizzati, tutto funzionale e curato. Niente docce fredde o disagi, qui ogni servizio funziona alla perfezione e contribuisce a un’esperienza perfetta. Un ambiente che unisce praticità e qualità, perfetto per il post partita.",
      image: images.spogliatoiArena,
      border: '#d68176'
    },
    {
      label: 'BEST SERVIZI',
      description: "Il bar di questa palestra è davvero eccezionale! Dalle centrifughe fresche e personalizzate agli snack salutari perfetti per il post-allenamento, c’è sempre qualcosa di gustoso e adatto a ogni esigenza. Ma non è solo il bar a fare la differenza: l’intera struttura offre servizi di alto livello, ben organizzati e pensati per il massimo comfort. Dall’accoglienza alla qualità degli spazi, tutto contribuisce a creare un’esperienza completa e piacevole. Un ambiente perfetto!",
      image: images.barArena,
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
      <p>Tutte le strutture sportive della Lombardia a portata di mano.</p>
    </div>
  </div>

  <CategorySelector />

  <section id="campi" class="anchor-target" aria-hidden="true"></section>
  <section id="spogliatoi" class="anchor-target" aria-hidden="true"></section>
  <section id="servizi" class="anchor-target" aria-hidden="true"></section>
  <section id="overall" class="anchor-target" aria-hidden="true"></section>

  <!-- SEZIONE HIGHLIGHTS -->
  <section class="highlights-section" id="reviews">
    <div class="section-header">
      <h2>I migliori del 2025</h2>
      <p>Scopri chi si è classificato al top in ogni categoria</p>
    </div>

    <div class="highlight-grid">
      {#each highlights as highlight}
        <div class="card-wrapper">
          <article class="highlight-card" style="background-color: {highlight.border}">
            <div class="new-badge">
              <div class="badge-circle" style="background-color: {highlight.border}">
                <span>2025</span>
              </div>
              <div class="badge-ribbon" style="background-color: {highlight.border}">
                {highlight.badgeLabel}
              </div>
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

          <!-- Sliding Block -->
          <div class="sliding-description" style="background-color: {highlight.border}dd">
            <p>{highlight.description}</p>
          </div>
        </div>
      {/each}
    </div>
    <a class="link-arrow" href="#reviews">Vedi di più <span>→</span></a>
  </section>

  <!-- SEZIONE ARENA -->
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
            <div class="rating-stars" style="color: {card.border};">★★★★★</div>
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
  /* BASE */
  .page-home {
    min-height: 100vh;
    font-family: var(--font-primary);
    background: var(--color-background-primary);
    color: var(--color-content-primary);
  }

  .section-header { text-align: center; margin-bottom: 48px; color: var(--color-content-primary); }
  .section-header h2 { font-size: 50px; font-weight: 600; margin: 0; }
  .section-header p { font-size: 26px; opacity: 0.9; }

  /* HERO */

  
  .hero-shell { 
    padding: 1px 24px; 
    text-align: center; 
    background: 
    linear-gradient(0deg, var(--color-background-primary) 30%, transparent 100%), 
    linear-gradient(90deg, #48acdc 20%, #d68176 50%, #f5d547 80%);}
  .hero-copy h1 { 
    font-size: clamp(4rem, 8vw, 6.5rem); 
    font-weight: 500; line-height: 0.8; 
    color: white; }
  .hero-tagline { font-size: 48px; font-weight: 600; color: var(--color-content-primary); margin-top: 10px; }
  .hero-copy p { font-size: 28px; max-width: 800px; margin: 20px auto; color: var(--color-content-primary); }

  /* HIGHLIGHTS SECTION */
  .highlights-section { background-color: var(--color-background-primary); padding: 120px 24px; }
  .highlight-grid { 
    display: grid; 
    grid-template-columns: repeat(auto-fit, 320px); 
    justify-content: center; 
    gap: 80px 40px; 
  }

  .card-wrapper {
    position: relative;
    display: flex;
    flex-direction: column;
  }

  .highlight-card {
    border-radius: 24px;
    position: relative;
    z-index: 11; /* Over the sliding block */
    color: var(--color-content-primary);
    padding: 8px;
    display: flex;
    flex-direction: column;
    background: var(--color-card-primary);
    border: 1px solid var(--color-border);
    transition: transform 0.3s ease;
  }

  /* SLIDING DESCRIPTION - Matched to image_f204a2.png */
  .sliding-description {
    position: absolute;
    /* bottom: 0; Align to bottom so it slides out from the edge */
    bottom: 0;
    z-index: 10; 
    
    /* Style matched to image_f204a2.png */
    background-color: var(--color-background-primary);
    color: var(--color-content-primary);
    padding: 12px; /* Extra top padding to handle the overlap */
    border: 4px solid var(--color-border);
    border-radius: 24px; /* Very rounded corners per the image */
    
    font-size: 16px;
    line-height: 1.4;
    font-weight: 500;
    
    /* Hidden State */
    transform: translateY(-10px);
    transition: transform 0.5s cubic-bezier(0.165, 0.84, 0.44, 1);
    pointer-events: none;
  }

  @media (hover: hover) {
    .card-wrapper:hover .sliding-description {
      opacity: 1;
      /* Slides down. 100% puts it exactly under the card */
      transform: translateY(100%); 
    }
    
    .card-wrapper:hover .highlight-card {
      /* Lift the card slightly to reveal the "drawer" sliding out */
      transform: translateY(-10px);
    }
  }

  @media (hover: none) {
    .card-wrapper { 
      margin-bottom: 120px; /* Make space so cards don't overlap on mobile */
    }
    .sliding-description {
      position: relative;
      transform: translateY(0);
      margin-top: -25px; /* Pull it up to "dock" with the card */
      padding-top: 35px;
      left: 0;
      right: 0;
      background-color: var(--color-background-strong) !important;
      border: 3px solid var(--color-border);
    }
  }

  /* BADGES & MEDIA */
  .new-badge { 
    position: absolute; 
    top: -25px; 
    left: -15px; 
    display: flex; 
    align-items: center; 
    z-index: 10; }
  .badge-circle { 
    width: 60px; 
    height: 60px; 
    border-radius: 50%; 
    border: 2px solid var(--color-border); 
    display: flex; align-items: center; 
    justify-content: center; 
    color: black; 
    background: var(--color-surface-strong); 
    font-weight: bold; }
  .badge-ribbon { 
    margin-left: -10px; 
    padding: 6px 15px; 
    color: black; 
    font-size: 11px; font-weight: bold; 
    clip-path: polygon(0 0, 95% 0, 100% 50%, 95% 100%, 0 100%); 
    background: var(--color-surface-strong); }
  
  .highlight-media img { width: 100%; aspect-ratio: 16/10; object-fit: cover; border-radius: 18px; margin-bottom: -12px; }
  .highlight-body { padding:0px 0px 4px 4px; }
  .highlight-title { font-size: 24px; font-weight: 600; margin-bottom: 4px; color: black; }
  .highlight-details { display: flex; gap: 8px; }
  .address-text p { margin: 0; font-size: 14px; line-height: 1.2; color: black; }
  .icon-pin { width: 14px; height: 18px; filter: brightness(0); margin-top: 4px; }

  /* ARENA SECTION */
  .arena-section { padding: 100px 24px; background: linear-gradient(180deg, var(--color-background-primary) 0%, #48acdc 20%, #d68176 50%, #f5d547 80%, var(--color-background-primary) 100%); position: relative; }
  .arena-grid { display: grid; grid-template-columns: repeat(auto-fit, 320px); justify-content: center; gap: 40px; position: relative; z-index: 2; }
  .arena-card { background: var(--color-card-primary); border: 2px solid var(--color-border); border-radius: 28px; overflow: hidden; display: flex; flex-direction: column; min-height: 480px; }
  .arena-media { padding: 8px 8px 0 8px; }
  .arena-media img { width: 100%; aspect-ratio: 16/10; object-fit: cover; border-radius: 20px; }
  .arena-body { padding: 12px; color: var(--color-content-primary); }
  .rating-stars { font-size: 32px; text-align: center; margin-bottom: 10px; letter-spacing: 5px; }

  /* UTILS */
  .gradient-overlay { position: absolute; left: 0; right: 0; height: 150px; z-index: 1; pointer-events: none; }
  .gradient-overlay.top { top: 0; background: linear-gradient(to bottom, var(--color-background-primary), transparent); }
  .gradient-overlay.bottom { bottom: 0; background: linear-gradient(to top, var(--color-background-primary), transparent); }
  .centered h2 { font-size: 60px; }
  .link-arrow { 
    display: block; 
    width: fit-content; 
    margin: 40px auto 0; 
    color: var(--color-content-primary); 
    font-size: 28px; 
    text-decoration: none; 
    position: relative; 
    z-index: 1; }
  .page-footer {
    padding: 40px 24px;
    background: black;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 14px;
  }

  .page-footer img {
    max-width: 220px;
    width: 100%;
    height: auto;
    display: block;
  }

  @media (max-width: 1150px) {
    .highlight-grid, .arena-grid { grid-template-columns: 1fr; max-width: 370px; margin: 0 auto; }
  }
</style>