<script>
  const metrics = [
    { name: 'Throughput', value: '2.4M req/s', bar: 94, accent: true },
    { name: 'Cache hit', value: '87%', bar: 87, accent: false },
    { name: 'DB connections', value: '412', bar: 62, accent: false },
    { name: 'Queue depth', value: 'Low', bar: 18, accent: false }
  ];
</script>

<div class="metrics-section">
  <header class="section-header">
    <h2 class="section-head">System health</h2>
    <p class="section-sub">Current capacity and resource usage</p>
  </header>
  <div class="metric-bars">
    {#each metrics as m}
      <div class="metric-row">
        <div class="metric-info">
          <span class="metric-name">{m.name}</span>
          <span class="metric-value" class:accent-red={m.accent}>{m.value}</span>
        </div>
        <div class="metric-track blueprint-border">
          <div
            class="metric-fill"
            class:metric-fill-red={m.accent}
            style="width: {m.bar}%"
          ></div>
        </div>
      </div>
    {/each}
  </div>
  <div class="footer-note blueprint-border">
    <span class="mono">Last updated: 2025-02-19 14:35 UTC</span>
    <span class="status accent-red">All systems operational</span>
  </div>
</div>

<style>
  .metrics-section {
    max-width: 620px;
    width: 100%;
    margin-left: max(calc(280px + 2rem), 2rem);
  }

  @media (max-width: 480px) {
    .metrics-section { margin-left: max(calc(240px + 1.5rem), 1.5rem); }
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
    text-shadow: 0 0 30px rgba(0, 212, 255, 0.2);
  }

  .section-sub {
    font-size: 0.9rem;
    color: var(--text-muted);
    margin: 0;
    letter-spacing: 0.02em;
  }

  .metric-bars {
    display: flex;
    flex-direction: column;
    gap: 1.35rem;
    margin-bottom: 2rem;
  }

  .metric-row {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
  }

  .metric-info {
    display: flex;
    justify-content: space-between;
    font-size: 0.9rem;
    align-items: baseline;
  }

  .metric-name {
    color: var(--text-muted);
    letter-spacing: 0.03em;
  }

  .metric-value {
    font-family: 'JetBrains Mono', monospace;
    color: var(--text);
    font-weight: 600;
    letter-spacing: 0.02em;
  }

  .metric-value.accent-red {
    color: var(--accent-red);
    text-shadow: 0 0 16px var(--accent-red-glow);
  }

  .metric-track {
    height: 10px;
    background: var(--bg-panel);
    border-radius: 4px;
    overflow: hidden;
  }

  .metric-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--blueprint-dim), var(--blueprint));
    border-radius: 4px;
    transition: width 0.5s ease;
  }

  .metric-fill.metric-fill-red {
    background: linear-gradient(90deg, var(--accent-red-dim), var(--accent-red));
    box-shadow: 0 0 20px var(--accent-red-glow);
  }

  .footer-note {
    padding: 0.9rem 1.25rem;
    background: var(--bg-glass);
    border-radius: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.82rem;
    color: var(--text-muted);
    backdrop-filter: blur(12px);
  }

  .footer-note .status.accent-red {
    color: var(--accent-red);
    font-weight: 500;
  }
</style>
