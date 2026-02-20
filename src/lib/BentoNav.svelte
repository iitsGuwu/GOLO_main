<script>
  function scrollToSection(id) {
    const viewport = document.querySelector('.scroll-viewport');
    const sections = ['hero', 'data', 'charts', 'metrics'];
    const index = sections.indexOf(id);
    if (viewport !== null && index >= 0) {
      viewport.scrollTo({ left: index * window.innerWidth, behavior: 'smooth' });
    }
  }
</script>

<aside class="bento" aria-label="Navigation and site info">
  <div class="bento-inner blueprint-border">
    <div class="col col-left">
      <div class="cell cell-home">
        <button type="button" class="cell-btn" on:click={() => scrollToSection('hero')}>Home</button>
      </div>
      <div class="cell cell-icons">
        <a href="https://x.com" target="_blank" rel="noopener noreferrer" class="icon-link" aria-label="X">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        </a>
        <a href="https://substack.com" target="_blank" rel="noopener noreferrer" class="icon-link" aria-label="Substack">
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M22.539 8.242H1.46V5.406h21.08v2.836zM1.46 10.812V24L12 18.11 22.54 24V10.812H1.46zM22.54 0H1.46v2.836h21.08V0z"/></svg>
        </a>
      </div>
    </div>
    <div class="col col-mid">
      <div class="cell cell-ep00">
        <button type="button" class="cell-btn" on:click={() => scrollToSection('data')}>EP00</button>
      </div>
      <div class="cell cell-experiment">
        <button type="button" class="cell-btn" on:click={() => scrollToSection('charts')}>Experiment</button>
      </div>
      <div class="cell cell-plan">
        <button type="button" class="cell-btn" on:click={() => scrollToSection('metrics')}>The plan</button>
      </div>
    </div>
    <div class="col col-right">
      <div class="cell cell-golo">
        <a href="https://golo.wtf" target="_blank" rel="noopener noreferrer" class="cell-link">$GOLO</a>
      </div>
      <div class="cell cell-gboy">
        <a href="https://gboy.golo.wtf" target="_blank" rel="noopener noreferrer" class="cell-link">GBOY</a>
      </div>
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
    display: flex;
    flex-direction: row;
    gap: 1px;
    background: var(--border);
    padding: 1px;
    width: 280px;
    min-height: 88px;
    border-radius: 6px;
    overflow: hidden;
    box-shadow: 0 6px 24px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(255, 0, 0, 0.08);
  }

  .col {
    display: flex;
    flex-direction: column;
    gap: 1px;
    flex: 1;
    min-width: 0;
  }

  .col-mid { flex: 1.5; }

  .col .cell {
    flex: 1;
    min-height: 0;
  }

  .cell {
    padding: 0.4rem 0.35rem;
    background: var(--bg-glass);
    backdrop-filter: blur(16px);
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.35rem;
    min-width: 0;
  }

  .cell-btn {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    color: var(--text-muted);
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
    width: 100%;
    text-align: center;
    transition: color 0.2s, text-shadow 0.2s;
  }

  .cell-btn:hover {
    color: var(--blueprint);
    text-shadow: 0 0 10px rgba(255, 0, 0, 0.3);
  }

  .cell-icons {
    flex-direction: row;
    justify-content: center;
    gap: 0.75rem;
  }

  .icon-link {
    display: flex;
    color: var(--text-muted);
    transition: color 0.2s;
  }

  .icon-link:hover {
    color: var(--accent-red);
  }

  .icon {
    width: 14px;
    height: 14px;
  }

  .cell-link {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    color: var(--text-muted);
    text-decoration: none;
    text-align: center;
    transition: color 0.2s, text-shadow 0.2s;
  }

  .cell-link:hover {
    color: var(--blueprint);
    text-shadow: 0 0 10px rgba(255, 0, 0, 0.3);
  }

  @media (max-width: 480px) {
    .bento {
      top: 0.6rem;
      left: 0.6rem;
    }
    .bento-inner {
      width: 240px;
      min-height: 88px;
    }
    .cell { padding: 0.3rem 0.25rem; }
    .cell-btn, .cell-link { font-size: 0.58rem; }
    .icon { width: 12px; height: 12px; }
  }
</style>
