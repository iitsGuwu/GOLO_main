<script>
  const barData = [72, 45, 88, 61, 94, 53, 78];
  const barLabels = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
  const linePoints = [30, 45, 40, 65, 55, 80, 70];
  const maxBar = Math.max(...barData);
  const maxLine = Math.max(...linePoints);
</script>

<div class="charts-section">
  <header class="section-header">
    <h2 class="section-head">Analytics</h2>
    <p class="section-sub">Weekly throughput and engagement</p>
  </header>
  <div class="charts-row">
    <div class="chart-panel blueprint-border">
      <h3>Requests by day</h3>
      <div class="bar-chart">
        {#each barData as val, i}
          <div class="bar-wrap">
            <div
              class="bar"
              class:accent-red={i === 4}
              style="height: {(val / maxBar) * 100}%"
            ></div>
            <span class="bar-label">{barLabels[i]}</span>
          </div>
        {/each}
      </div>
    </div>
    <div class="chart-panel blueprint-border">
      <h3>Latency trend (ms)</h3>
      <div class="line-chart">
        <svg viewBox="0 0 280 120" preserveAspectRatio="none">
          {#each linePoints as p, i}
            {#if i > 0}
              <line
                x1={(i - 1) * (280 / (linePoints.length - 1))}
                y1={120 - (linePoints[i - 1] / maxLine) * 100}
                x2={i * (280 / (linePoints.length - 1))}
                y2={120 - (p / maxLine) * 100}
                class="line-seg"
                class:line-red={i === linePoints.length - 1}
              />
            {/if}
          {/each}
          {#each linePoints as p, i}
            <circle
              cx={i * (280 / (linePoints.length - 1))}
              cy={120 - (p / maxLine) * 100}
              r="4"
              class="line-dot"
              class:dot-red={i === linePoints.length - 1}
            />
          {/each}
        </svg>
        <div class="line-labels">
          {#each barLabels as l}<span>{l}</span>{/each}
        </div>
      </div>
    </div>
  </div>
  <div class="donut-wrap blueprint-border">
    <h3>Traffic split</h3>
    <div class="donut-chart">
      <svg viewBox="0 0 100 100">
        <circle cx="50" cy="50" r="40" fill="none" stroke="var(--bg-panel)" stroke-width="12" />
        <circle cx="50" cy="50" r="40" fill="none" stroke="var(--accent-red)" stroke-width="12"
          stroke-dasharray="75 226" stroke-dashoffset="0" />
        <circle cx="50" cy="50" r="40" fill="none" stroke="var(--blueprint)" stroke-width="12"
          stroke-dasharray="60 226" stroke-dashoffset="-75" />
        <circle cx="50" cy="50" r="40" fill="none" stroke="#22c55e" stroke-width="12"
          stroke-dasharray="50 226" stroke-dashoffset="-135" />
        <circle cx="50" cy="50" r="40" fill="none" stroke="#eab308" stroke-width="12"
          stroke-dasharray="41 226" stroke-dashoffset="-185" />
      </svg>
    </div>
    <div class="donut-legend">
      <span class="accent-red"><i style="background: var(--accent-red)"></i> API 33%</span>
      <span><i style="background: var(--blueprint)"></i> Web 26%</span>
      <span><i style="background: #22c55e"></i> Mobile 22%</span>
      <span><i style="background: #eab308"></i> Other 18%</span>
    </div>
  </div>
</div>

<style>
  .charts-section {
    max-width: 960px;
    width: 100%;
    margin-left: max(calc(280px + 2rem), 2rem);
  }

  @media (max-width: 480px) {
    .charts-section { margin-left: max(calc(240px + 1.5rem), 1.5rem); }
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

  .charts-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-bottom: 1.5rem;
  }

  @media (max-width: 700px) {
    .charts-row { grid-template-columns: 1fr; }
  }

  .chart-panel {
    background: var(--bg-glass);
    padding: 1.5rem;
    border-radius: 4px;
    backdrop-filter: blur(12px);
  }

  .chart-panel h3 {
    margin: 0 0 1.25rem;
    font-size: 0.8rem;
    color: var(--text-muted);
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  .bar-chart {
    display: flex;
    align-items: flex-end;
    gap: 0.5rem;
    height: 140px;
  }

  .bar-wrap {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
  }

  .bar {
    width: 100%;
    max-width: 36px;
    min-height: 4px;
    background: linear-gradient(to top, var(--blueprint-dim), var(--blueprint));
    border-radius: 4px 4px 0 0;
    transition: height 0.4s ease;
  }

  .bar.accent-red {
    background: linear-gradient(to top, var(--accent-red-dim), var(--accent-red));
    box-shadow: 0 0 16px var(--accent-red-glow);
  }

  .bar-label {
    font-size: 0.7rem;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
  }

  .line-chart svg {
    width: 100%;
    height: 120px;
    display: block;
  }

  .line-seg {
    stroke: var(--blueprint);
    stroke-width: 2;
    fill: none;
  }

  .line-seg.line-red {
    stroke: var(--accent-red);
  }

  .line-dot {
    fill: var(--blueprint);
    stroke: var(--bg-dark);
    stroke-width: 1.5;
  }

  .line-dot.dot-red {
    fill: var(--accent-red);
    stroke: var(--bg-dark);
    filter: drop-shadow(0 0 6px var(--accent-red-glow));
  }

  .line-labels {
    display: flex;
    justify-content: space-between;
    margin-top: 0.35rem;
    font-size: 0.7rem;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
  }

  .donut-wrap {
    background: var(--bg-glass);
    padding: 1.5rem;
    border-radius: 4px;
    display: flex;
    align-items: center;
    gap: 2rem;
    flex-wrap: wrap;
    backdrop-filter: blur(12px);
  }

  .donut-wrap h3 {
    margin: 0 0 0.5rem;
    font-size: 0.8rem;
    color: var(--text-muted);
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    width: 100%;
  }

  .donut-chart svg {
    width: 120px;
    height: 120px;
  }

  .donut-legend {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    font-size: 0.85rem;
    color: var(--text-muted);
  }

  .donut-legend span.accent-red {
    color: var(--accent-red);
  }

  .donut-legend i {
    display: inline-block;
    width: 10px;
    height: 10px;
    margin-right: 0.5rem;
    border-radius: 2px;
    vertical-align: middle;
  }
</style>
