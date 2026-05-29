<template>
  <section class="proof-grid">
    <article class="panel proof-panel">
      <header class="panel-header">
        <div>
          <h2>Proof Sprint</h2>
          <span>{{ sprint.window }}</span>
        </div>
        <button class="icon-button" title="Export proof sprint">
          <i data-lucide="target"></i>
        </button>
      </header>
      <p class="proof-objective">{{ sprint.objective }}</p>
      <div class="proof-metrics">
        <article v-for="metric in sprint.metrics" :key="metric.label" class="proof-metric">
          <div>
            <strong>{{ metric.label }}</strong>
            <span>{{ metric.current }}/{{ metric.target }} - {{ metric.status }}</span>
          </div>
          <div class="progress-track">
            <div :style="{ width: progress(metric) + '%' }"></div>
          </div>
        </article>
      </div>
    </article>

    <article class="panel proof-panel">
      <header class="panel-header">
        <h2>Execution</h2>
        <button class="icon-button" title="Open execution runbook">
          <i data-lucide="route"></i>
        </button>
      </header>
      <div class="proof-steps">
        <article v-for="step in sprint.steps" :key="step.day + step.title" class="proof-step">
          <span>{{ step.day }}</span>
          <div>
            <strong>{{ step.title }}</strong>
            <p>{{ step.owner }} - {{ step.status }}</p>
          </div>
        </article>
      </div>
    </article>

    <article class="panel proof-panel wide-proof">
      <header class="panel-header">
        <h2>Win Conditions</h2>
        <button class="icon-button" title="Open judge guide">
          <i data-lucide="badge-check"></i>
        </button>
      </header>
      <div class="win-list">
        <article v-for="item in sprint.winConditions" :key="item" class="win-item">
          <i data-lucide="check"></i>
          <span>{{ item }}</span>
        </article>
      </div>
    </article>
  </section>
</template>

<script>
export default {
  props: {
    sprint: { type: Object, required: true },
  },
  methods: {
    progress(metric) {
      if (!metric.target) return 0;
      return Math.min(100, Math.round((metric.current / metric.target) * 100));
    },
  },
};
</script>
