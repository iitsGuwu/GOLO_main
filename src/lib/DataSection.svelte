<script>
  // EP00: Pilote episode – experimental layout
</script>

<div class="pilote-section">
  <div class="section-gutter" aria-hidden="true"></div>
  <div class="section-content">
  <header class="section-header">
    <span class="ep-tag">EP00</span>
    <h2 class="section-head">Pilote episode</h2>
    <p class="section-sub">The first experiment</p>
  </header>

  <div class="experiment-grid">
    <div class="block block-state blueprint-border">
      <span class="block-num">01</span>
      <h3>Current state</h3>
      <p>gboy.golo.wtf is the live testbed: an autonomous AI agent that launches its own token. The project captures the current architecture, agent behaviour, and token flow before any burn mechanics were introduced.</p>
    </div>

    <div class="block block-experiment blueprint-border accent-red-border">
      <span class="block-num accent-red">02</span>
      <h3>Burn engine · experiment</h3>
      <p>We ran experiments and tests around the burn engine idea—how to attach a programmable burn mechanism to an agent’s token launch, and how that affects supply, incentives, and on-chain behaviour.</p>
    </div>

    <div class="block block-pow blueprint-border">
      <span class="block-num">03</span>
      <h3>Proof of work & benefits</h3>
      <p>Proof of work: the burn engine was validated in this pilote. Benefits for an autonomous AI agent’s token launch flow include aligned incentives, deflationary pressure, and a clear “fuel” narrative that ties token use to value creation and future phases.</p>
    </div>
  </div>

  <div class="lab-footer blueprint-border">
    <span class="mono">gboy.golo.wtf</span>
    <span class="muted">· Pilote · Burn engine v0</span>
  </div>
  </div>
</div>

<style>
  .pilote-section {
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
    max-width: 900px;
  }

  @media (max-width: 600px) {
    .pilote-section {
      grid-template-columns: minmax(0, calc(240px + 1.5rem)) minmax(0, 1fr);
    }
  }

  @media (max-width: 400px) {
    .pilote-section {
      grid-template-columns: 1fr;
    }
    .section-gutter { display: none; }
    .section-content { max-width: none; }
  }

  .section-header {
    margin-bottom: 2rem;
  }

  .ep-tag {
    display: inline-block;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent-red);
    letter-spacing: 0.2em;
    margin-bottom: 0.35rem;
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
    font-size: 0.95rem;
    color: var(--text-muted);
    margin: 0;
    letter-spacing: 0.02em;
  }

  .experiment-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto auto;
    grid-template-areas:
      'state experiment'
      'pow pow';
    gap: 1rem;
    margin-bottom: 1.5rem;
  }

  @media (max-width: 640px) {
    .experiment-grid {
      grid-template-columns: 1fr;
      grid-template-areas: 'state' 'experiment' 'pow';
    }
  }

  .block {
    padding: 1.25rem;
    background: var(--bg-glass);
    border-radius: 4px;
    position: relative;
    backdrop-filter: blur(12px);
  }

  .block-num {
    position: absolute;
    top: 0.75rem;
    right: 0.75rem;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--blueprint-dim);
    letter-spacing: 0.1em;
  }

  .block h3 {
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--blueprint);
    margin: 0 0 0.6rem;
    letter-spacing: 0.04em;
    padding-right: 2rem;
  }

  .block p {
    font-size: 0.88rem;
    line-height: 1.55;
    color: var(--text-muted);
    margin: 0;
  }

  .block-state { grid-area: state; }
  .block-experiment { grid-area: experiment; }
  .block-pow { grid-area: pow; }

  .lab-footer {
    padding: 0.75rem 1rem;
    background: var(--bg-glass);
    border-radius: 4px;
    font-size: 0.8rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .lab-footer .mono { color: var(--blueprint); }
  .lab-footer .muted { color: var(--text-muted); }
</style>
