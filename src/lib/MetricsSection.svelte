<script>
  // What's next – EP01 & EP01.5 teasers
</script>

<div class="next-section">
  <div class="section-gutter" aria-hidden="true"></div>
  <div class="section-content">
  <header class="section-header">
    <h2 class="section-head">What's next</h2>
    <p class="section-sub">EP01 & EP01.5</p>
  </header>

  <div class="next-split">
    <div class="next-block blueprint-border">
      <span class="block-ep">EP01</span>
      <p class="hint">A key has been acquired. What it opens remains to be seen.</p>
      <span class="mono cipher">[ KEY_ACQUIRED ]</span>
    </div>
    <div class="next-block blueprint-border accent-red-border">
      <span class="block-ep accent-red">EP01.5</span>
      <p class="hint">gboy BURN's. Something is heating up.</p>
      <span class="mono cipher">[ BURN_SIGNAL ]</span>
    </div>
  </div>
  </div>
</div>

<style>
  .next-section {
    display: grid;
    grid-template-columns: minmax(0, calc(280px + 2rem)) minmax(0, 1fr);
    width: 100%;
    max-width: 100%;
    min-width: 0;
  }

  .section-gutter {
    min-width: 0;
  }

  .section-content {
    padding: clamp(1.5rem, 4vw, 3rem);
    padding-left: clamp(1rem, 3vw, 2rem);
    min-width: 0;
    max-width: 820px;
  }

  @media (max-width: 600px) {
    .next-section {
      grid-template-columns: minmax(0, calc(240px + 1.5rem)) minmax(0, 1fr);
    }
  }

  @media (max-width: 400px) {
    .next-section {
      grid-template-columns: 1fr;
    }
    .section-gutter { display: none; }
    .section-content { max-width: none; }
  }

  .section-header {
    margin-bottom: 2rem;
  }

  .section-head {
    font-size: clamp(1.5rem, 4vw, 1.85rem);
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin: 0 0 0.35rem;
    color: var(--blueprint);
    text-shadow: 0 0 30px rgba(255, 0, 0, 0.2);
  }

  .section-sub {
    font-size: 0.9rem;
    color: var(--text-muted);
    margin: 0;
    letter-spacing: 0.12em;
  }

  .next-split {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.25rem;
  }

  @media (max-width: 640px) {
    .next-split { grid-template-columns: 1fr; }
  }

  .next-block {
    padding: 1.5rem;
    background: var(--bg-glass);
    border-radius: 4px;
    backdrop-filter: blur(12px);
  }

  .block-ep {
    display: inline-block;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--blueprint);
    letter-spacing: 0.2em;
    margin-bottom: 0.75rem;
  }

  .next-block .hint {
    font-size: 0.95rem;
    line-height: 1.55;
    color: var(--text);
    margin: 0 0 1rem;
    letter-spacing: 0.02em;
  }

  .cipher {
    font-size: 0.72rem;
    color: var(--blueprint-dim);
    letter-spacing: 0.08em;
  }

  .next-block.accent-red-border .cipher {
    color: var(--accent-red-dim);
  }
</style>
