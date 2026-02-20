<script>
  import ModelViewer from "./ModelViewer.svelte";
  // Blueprint text boxes branch out from center
</script>

<div class="hero">
  <div class="center-zone">
    <div class="cube-scene">
      <ModelViewer />
    </div>
  </div>

  <!-- Blueprint branches: lines + label boxes -->
  <svg class="blueprint-lines" viewBox="0 0 100 100" preserveAspectRatio="none">
    <defs>
      <marker
        id="arrow"
        markerWidth="4"
        markerHeight="4"
        refX="3"
        refY="2"
        orient="auto"
      >
        <path d="M0,0 L4,2 L0,4 Z" fill="var(--blueprint)" opacity="0.8" />
      </marker>
    </defs>
    <line x1="50" y1="50" x2="15" y2="25" class="branch" />
    <line x1="50" y1="50" x2="85" y2="20" class="branch" />
    <line x1="50" y1="50" x2="88" y2="55" class="branch" />
    <line x1="50" y1="50" x2="80" y2="88" class="branch" />
    <line x1="50" y1="50" x2="20" y2="85" class="branch" />
    <line x1="50" y1="50" x2="12" y2="52" class="branch" />
  </svg>

  <div class="label label-tl blueprint-border accent-red-border">
    <span class="label-id"><span class="accent-red">A-01</span></span>
    <span class="label-title">Core System</span>
    <span class="label-desc"
      >Primary module · <span class="accent-red">Active</span></span
    >
  </div>
  <div class="label label-tr blueprint-border">
    <span class="label-id">B-02</span>
    <span class="label-title">Data Pipeline</span>
    <span class="label-desc">Throughput 2.4M/s</span>
  </div>
  <div class="label label-mr blueprint-border">
    <span class="label-id">C-03</span>
    <span class="label-title">API Gateway</span>
    <span class="label-desc">Latency &lt;12ms</span>
  </div>
  <div class="label label-br blueprint-border">
    <span class="label-id">D-04</span>
    <span class="label-title">Storage Layer</span>
    <span class="label-desc">99.99% uptime</span>
  </div>
  <div class="label label-bl blueprint-border">
    <span class="label-id">E-05</span>
    <span class="label-title">Analytics</span>
    <span class="label-desc">Real-time dash</span>
  </div>
  <div class="label label-ml blueprint-border">
    <span class="label-id">F-06</span>
    <span class="label-title">Security</span>
    <span class="label-desc">Zero-trust</span>
  </div>

  <div class="hero-title">
    <h1>GOLO<span class="title-dot">.</span></h1>
    <p class="tagline">System blueprint · v2.0</p>
  </div>
</div>

<style>
  .hero {
    position: relative;
    width: 100%;
    min-height: 80vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-left: max(calc(280px + 2rem), 2rem);
  }

  @media (max-width: 480px) {
    .hero {
      padding-left: max(calc(240px + 1.5rem), 1.5rem);
    }
  }

  .center-zone {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 2;
  }

  .cube-scene {
    perspective: 800px;
    width: 650px;
    height: 650px;
  }

  .blueprint-lines {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
  }

  .branch {
    stroke: var(--blueprint);
    stroke-width: 0.4;
    stroke-dasharray: 2 1.5;
    opacity: 0.7;
    animation: dash 20s linear infinite;
  }

  @keyframes dash {
    to {
      stroke-dashoffset: -100;
    }
  }

  .label {
    position: absolute;
    padding: 0.5rem 0.75rem;
    min-width: 120px;
    background: rgba(15, 33, 55, 0.92);
    font-family: "JetBrains Mono", monospace;
    z-index: 3;
    display: flex;
    flex-direction: column;
    gap: 0.15rem;
  }

  .label-id {
    font-size: 0.65rem;
    color: var(--blueprint);
    letter-spacing: 0.1em;
  }

  .label-title {
    font-size: 0.8rem;
    font-weight: 600;
    color: var(--text);
  }

  .label-desc {
    font-size: 0.65rem;
    color: var(--text-muted);
  }

  .label-tl {
    left: 8%;
    top: 18%;
  }
  .label-tr {
    right: 6%;
    top: 15%;
  }
  .label-mr {
    right: 4%;
    top: 48%;
  }
  .label-br {
    left: 80%;
    bottom: 8%;
  }
  .label-bl {
    right: 80%;
    bottom: 12%;
  }
  .label-ml {
    left: 4%;
    top: 48%;
  }

  .hero-title {
    position: absolute;
    bottom: 10%;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;
    z-index: 4;
  }

  .hero-title h1 {
    margin: 0;
    font-size: clamp(2rem, 6vw, 3.5rem);
    font-weight: 700;
    letter-spacing: 0.35em;
    color: var(--blueprint);
    text-shadow: 0 0 40px rgba(255, 0, 0, 0.3);
  }

  .title-dot {
    color: var(--accent-red);
    text-shadow: 0 0 20px var(--accent-red-glow);
  }

  .accent-red {
    color: var(--accent-red);
  }

  .tagline {
    margin: 0.25rem 0 0;
    font-size: 0.8rem;
    color: var(--blueprint-dim);
    letter-spacing: 0.2em;
    font-family: "JetBrains Mono", monospace;
  }

  @media (max-width: 768px) {
    .label {
      min-width: 100px;
      padding: 0.4rem 0.5rem;
      font-size: 0.7rem;
    }
    .label-tl {
      left: 2%;
      top: 12%;
    }
    .label-tr {
      right: 2%;
      top: 10%;
    }
    .label-mr {
      right: 2%;
      top: 50%;
    }
    .label-br {
      left: 72%;
      bottom: 6%;
    }
    .label-bl {
      right: 72%;
      bottom: 10%;
    }
    .label-ml {
      left: 2%;
      top: 50%;
    }
    .cube-scene {
      width: 80vw;
      height: 80vw;
      max-width: 400px;
      max-height: 400px;
    }
  }
</style>
