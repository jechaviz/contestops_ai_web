<template>
  <section class="battle-grid">
    <article class="panel">
      <header class="panel-header">
        <h2>Judge Score</h2>
        <button class="icon-button" title="Export scorecard">
          <i data-lucide="clipboard-check"></i>
        </button>
      </header>
      <div class="score-list">
        <article v-for="item in scorecard" :key="item.label" class="score-row">
          <div>
            <strong>{{ item.label }}</strong>
            <span>{{ item.gap }}</span>
          </div>
          <meter min="0" max="100" :value="item.score"></meter>
          <b>{{ item.score }}</b>
        </article>
      </div>
    </article>

    <article class="panel">
      <header class="panel-header">
        <h2>Competitors</h2>
        <button class="icon-button" title="Open battlecard">
          <i data-lucide="swords"></i>
        </button>
      </header>
      <div class="competitor-list">
        <article v-for="item in competitors" :key="item.name" class="competitor-row">
          <span class="threat">{{ item.threat }}</span>
          <div>
            <strong>{{ item.name }}</strong>
            <p>{{ item.counter }}</p>
          </div>
        </article>
      </div>
    </article>
  </section>
</template>

<script>
export default {
  props: {
    scorecard: { type: Array, required: true },
    competitors: { type: Array, required: true },
  },
};
</script>
