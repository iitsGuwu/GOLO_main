<script>
  // $GOLO – Fueling a flame: past use + future treasury
</script>

<div class="golo-section">
  <div class="section-gutter" aria-hidden="true"></div>
  <div class="section-content">
  <header class="section-header">
    <h2 class="section-head">$GOLO</h2>
    <p class="section-sub">Fueling a flame</p>
  </header>

  <div class="golo-split">
    <div class="half blueprint-border">
      <div class="half-label">Then</div>
      <h3>Token use in the build</h3>
      <p>$GOLO was used in the gboy.golo.wtf build to fuel the autonomous agent’s token launch and operations. The token acted as the economic layer for the pilote: allocation, incentives, and on-chain actions were tied to $GOLO, proving the burn engine in a real deployment.</p>
    </div>
    <div class="half blueprint-border accent-red-border">
      <div class="half-label accent-red">Next</div>
      <h3>Development treasury</h3>
      <p>$GOLO will power GOLO’s growth as a development treasury: funding next phases, rewarding contributors, and sustaining the ecosystem. The same token that fueled the pilote becomes the reserve for building the next chapters—burn to mint, heists, and beyond.</p>
    </div>
  </div>

  <div class="flame-bar">
    <span class="mono">$GOLO</span>
    <span class="flame-dots">◆ ◆ ◆</span>
    <span class="muted">past → future</span>
  </div>
  </div>
</div>

<style>
  .golo-section {
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
    max-width: 920px;
  }

  @media (max-width: 600px) {
    .golo-section {
      grid-template-columns: minmax(0, calc(240px + 1.5rem)) minmax(0, 1fr);
    }
  }

  @media (max-width: 400px) {
    .golo-section {
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
    margin: 0 0 0.35rem;
    color: var(--blueprint);
    text-shadow: 0 0 30px rgba(255, 0, 0, 0.2);
  }

  .section-sub {
    font-size: 0.95rem;
    color: var(--text-muted);
    margin: 0;
    letter-spacing: 0.02em;
  }

  .golo-split {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.25rem;
    margin-bottom: 1.25rem;
  }

  @media (max-width: 640px) {
    .golo-split { grid-template-columns: 1fr; }
  }

  .half {
    padding: 1.5rem;
    background: var(--bg-glass);
    border-radius: 4px;
    backdrop-filter: blur(12px);
  }

  .half-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    color: var(--blueprint-dim);
    margin-bottom: 0.75rem;
  }

  .half h3 {
    font-size: 0.95rem;
    font-weight: 600;
    color: var(--text);
    margin: 0 0 0.6rem;
    letter-spacing: 0.03em;
  }

  .half p {
    font-size: 0.88rem;
    line-height: 1.55;
    color: var(--text-muted);
    margin: 0;
  }

  .flame-bar {
    padding: 0.7rem 1rem;
    background: var(--bg-glass);
    border-radius: 4px;
    border: 1px dashed var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.75rem;
    font-size: 0.8rem;
  }

  .flame-bar .mono { color: var(--blueprint); }
  .flame-dots { color: var(--accent-red); font-size: 0.6rem; letter-spacing: 0.3em; }
  .flame-bar .muted { color: var(--text-muted); }
</style>
