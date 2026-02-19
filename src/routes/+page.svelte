<script>
  import { onMount } from 'svelte';
  import Hero from '$lib/Hero.svelte';
  import DataSection from '$lib/DataSection.svelte';
  import ChartsSection from '$lib/ChartsSection.svelte';
  import MetricsSection from '$lib/MetricsSection.svelte';

  let scrollEl;

  onMount(() => {
    const el = scrollEl;
    if (!el) return;
    const onWheel = (e) => {
      if (e.deltaY !== 0) {
        e.preventDefault();
        el.scrollLeft += e.deltaY;
      }
    };
    el.addEventListener('wheel', onWheel, { passive: false });
    return () => el.removeEventListener('wheel', onWheel);
  });
</script>

<div class="scroll-viewport" bind:this={scrollEl}>
  <div class="scroll-wrapper">
    <section class="section blueprint-bg" id="hero">
      <Hero />
    </section>
    <section class="section blueprint-bg" id="data">
      <DataSection />
    </section>
    <section class="section blueprint-bg" id="charts">
      <ChartsSection />
    </section>
    <section class="section blueprint-bg" id="metrics">
      <MetricsSection />
    </section>
  </div>
</div>

<style>
  .scroll-viewport {
    cursor: grab;
    user-select: none;
  }
  .scroll-viewport:active {
    cursor: grabbing;
  }
</style>
