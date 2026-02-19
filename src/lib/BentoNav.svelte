<script>
  const sections = [
    { id: 'hero', label: 'Home' },
    { id: 'data', label: 'Data' },
    { id: 'charts', label: 'Analytics' },
    { id: 'metrics', label: 'Health' }
  ];

  function scrollToSection(id) {
    const el = document.getElementById(id);
    const viewport = document.querySelector('.scroll-viewport');
    if (el && viewport) {
      const index = sections.findIndex((s) => s.id === id);
      const sectionWidth = window.innerWidth;
      viewport.scrollTo({ left: index * sectionWidth, behavior: 'smooth' });
    }
  }
</script>

<aside class="bento" aria-label="Navigation and site info">
  <div class="bento-inner blueprint-border">
    <div class="cell cell-logo">
      <button type="button" class="logo logo-btn" on:click={() => scrollToSection('hero')}>GOLO</button>
    </div>
    <div class="cell cell-nav">
      <nav class="nav">
        {#each sections as s}
          <button type="button" class="nav-link" on:click={() => scrollToSection(s.id)}>{s.label}</button>
        {/each}
      </nav>
    </div>
    <div class="cell cell-contact">
      <span class="cell-label">Contact</span>
      <a href="mailto:hello@golo.dev" class="link" title="hello@golo.dev">Mail</a>
    </div>
    <div class="cell cell-legal">
      <span class="cell-label">Legal</span>
      <a href="/privacy" class="link">Privacy</a>
      <span class="sep">·</span>
      <a href="/terms" class="link">Terms</a>
    </div>
    <div class="cell cell-copy">
      <span class="mono">© 2025</span>
    </div>
    <div class="cell cell-status">
      <span class="status-dot" aria-hidden="true"></span>
      <span class="mono">Live</span>
    </div>
  </div>
</aside>

<style>
  .bento {
    position: fixed;
    top: 1rem;
    left: 1rem;
    z-index: 100;
    pointer-events: none;
  }

  .bento-inner {
    pointer-events: auto;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 1px;
    background: var(--border);
    padding: 1px;
    width: 280px;
    min-height: 52px;
    border-radius: 6px;
    overflow: hidden;
    box-shadow: 0 6px 24px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(0, 212, 255, 0.08);
  }

  .cell {
    padding: 0.28rem 0.4rem;
    background: var(--bg-glass);
    backdrop-filter: blur(16px);
    display: flex;
    flex-direction: column;
    gap: 0.08rem;
    justify-content: center;
    min-height: 0;
    overflow: hidden;
  }

  .cell-logo {
    grid-column: 1;
    grid-row: 1;
    border-radius: 5px 0 0 0;
  }

  .cell-nav {
    grid-column: 2;
    grid-row: 1;
    flex-direction: row;
    flex-wrap: wrap;
    flex-wrap: wrap;
    align-items: center;
    gap: 0.1rem;
  }

  .cell-contact {
    grid-column: 1;
    grid-row: 2;
    border-radius: 0 0 0 5px;
  }

  .cell-legal {
    grid-column: 2;
    grid-row: 2;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    gap: 0.15rem;
  }

  .cell-copy {
    grid-column: 3;
    grid-row: 1;
    border-radius: 0 5px 0 0;
  }

  .cell-status {
    grid-column: 3;
    grid-row: 2;
    flex-direction: row;
    align-items: center;
    gap: 0.28rem;
    border-radius: 0 0 5px 0;
  }

  .logo-btn {
    font: inherit;
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
  }

  .logo {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    color: var(--blueprint);
    transition: color 0.2s, text-shadow 0.2s;
  }

  .logo:hover,
  .logo-btn:hover {
    color: var(--accent-red);
    text-shadow: 0 0 12px var(--accent-red-glow);
  }

  .cell-label {
    font-size: 0.5rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--blueprint-dim);
  }

  .nav {
    display: flex;
    flex-wrap: wrap;
    gap: 0.15rem;
  }

  .nav-link {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.58rem;
    color: var(--text-muted);
    background: none;
    border: none;
    padding: 0.15rem 0.28rem;
    cursor: pointer;
    border-radius: 2px;
    transition: color 0.2s, background 0.2s;
  }

  .nav-link:hover {
    color: var(--blueprint);
    background: rgba(0, 212, 255, 0.08);
  }

  .link {
    font-size: 0.6rem;
    color: var(--text-muted);
    text-decoration: none;
    transition: color 0.2s;
  }

  .link:hover {
    color: var(--accent-red);
  }

  .sep {
    font-size: 0.7rem;
    color: var(--border);
  }

  .mono {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.58rem;
    color: var(--text-muted);
  }

  .status-dot {
    width: 4px;
    height: 4px;
    border-radius: 50%;
    background: var(--accent-red);
    box-shadow: 0 0 8px var(--accent-red-glow);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.6; }
  }

  @media (max-width: 480px) {
    .bento {
      top: 0.6rem;
      left: 0.6rem;
    }
    .bento-inner {
      width: 240px;
      min-height: 46px;
    }
    .cell { padding: 0.22rem 0.3rem; }
    .logo { font-size: 0.62rem; }
    .nav-link { font-size: 0.5rem; padding: 0.08rem 0.18rem; }
  }
</style>
