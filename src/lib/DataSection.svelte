<script>
  const stats = [
    { label: 'Active users', value: '124,892', change: '+12%', up: true, accent: true },
    { label: 'API calls (24h)', value: '2.4M', change: '+8%', up: true, accent: false },
    { label: 'Avg. response', value: '11ms', change: '-3ms', up: true, accent: false },
    { label: 'Error rate', value: '0.02%', change: '-0.01%', up: true, accent: false },
    { label: 'Uptime', value: '99.99%', change: null, up: null, accent: false }
  ];
</script>

<div class="data-section">
  <header class="section-header">
    <h2 class="section-head">Live data</h2>
    <p class="section-sub">Real-time system metrics and KPIs</p>
  </header>
  <div class="cards">
    {#each stats as item}
      <div class="card blueprint-border" class:accent-red-border={item.accent}>
        <span class="card-label">{item.label}</span>
        <span class="card-value" class:accent-red={item.accent}>{item.value}</span>
        {#if item.change}
          <span class="card-change" class:up={item.up} class:down={item.up === false}>{item.change}</span>
        {/if}
      </div>
    {/each}
  </div>
  <div class="data-grid blueprint-border">
    <div class="grid-header">
      <span>Event log (sample)</span>
      <span class="mono">ID · Timestamp · Type</span>
    </div>
    <div class="grid-row"><span>evt_8f2a</span><span>2025-02-19 14:32:01 UTC</span><span class="accent-red">auth</span></div>
    <div class="grid-row"><span>evt_9b1c</span><span>2025-02-19 14:31:58 UTC</span><span>api</span></div>
    <div class="grid-row"><span>evt_3d4e</span><span>2025-02-19 14:31:55 UTC</span><span>sync</span></div>
    <div class="grid-row"><span>evt_7a6f</span><span>2025-02-19 14:31:52 UTC</span><span class="accent-red">auth</span></div>
    <div class="grid-row"><span>evt_2c8d</span><span>2025-02-19 14:31:48 UTC</span><span>api</span></div>
  </div>
</div>

<style>
  .data-section {
    max-width: 920px;
    width: 100%;
    margin-left: max(calc(280px + 2rem), 2rem);
  }

  @media (max-width: 480px) {
    .data-section { margin-left: max(calc(240px + 1.5rem), 1.5rem); }
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

  .cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 1rem;
    margin-bottom: 2rem;
  }

  .card {
    padding: 1.25rem;
    background: var(--bg-glass);
    border-radius: 4px;
    display: flex;
    flex-direction: column;
    gap: 0.35rem;
    transition: box-shadow 0.2s ease, border-color 0.2s ease;
  }

  .card:hover {
    box-shadow: 0 0 0 1px rgba(0, 212, 255, 0.15);
  }

  .card-label {
    font-size: 0.7rem;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .card-value {
    font-size: 1.6rem;
    font-weight: 700;
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 0.02em;
  }

  .card-value.accent-red {
    color: var(--accent-red);
    text-shadow: 0 0 20px var(--accent-red-glow);
  }

  .card-change {
    font-size: 0.75rem;
    font-family: 'JetBrains Mono', monospace;
  }

  .card-change.up { color: #22c55e; }
  .card-change.down { color: #ef4444; }

  .data-grid {
    background: var(--bg-glass);
    border-radius: 4px;
    overflow: hidden;
  }

  .grid-header {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    gap: 1rem;
    padding: 0.85rem 1.25rem;
    background: rgba(0, 212, 255, 0.06);
    font-size: 0.78rem;
    color: var(--blueprint-dim);
    letter-spacing: 0.04em;
  }

  .grid-row {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    gap: 1rem;
    padding: 0.6rem 1.25rem;
    font-size: 0.85rem;
    border-top: 1px solid var(--border);
    font-family: 'JetBrains Mono', monospace;
  }

  .grid-row span:first-child { color: var(--blueprint); }
  .grid-row span:last-child:not(.accent-red) { color: var(--text-muted); }

  .grid-row .accent-red {
    color: var(--accent-red);
  }
</style>
