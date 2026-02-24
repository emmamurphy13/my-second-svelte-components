<script>
  export let facts = [];
  let currentFactIndex = 0;

  function nextFact() {
    if (facts.length > 0) {
      currentFactIndex = (currentFactIndex + 1) % facts.length;
    }
  }

  function previousFact() {
    if (facts.length > 0) {
      currentFactIndex = (currentFactIndex - 1 + facts.length) % facts.length;
    }
  }

  $: currentFact = facts.length > 0 ? facts[currentFactIndex] : null;
</script>

<aside class="fun-fact-panel">
  <div class="panel-header">
    <h3 class="panel-title">Did You Know?</h3>
    <div class="decorative-line"></div>
  </div>

  {#if currentFact}
    <div class="fact-content">
      <p class="fact-text">{currentFact.text}</p>
      {#if currentFact.source}
        <p class="fact-source">— {currentFact.source}</p>
      {/if}
    </div>

    {#if facts.length > 1}
      <div class="fact-controls">
        <button class="fact-button prev" on:click={previousFact} aria-label="Previous fact">
          ←
        </button>
        <div class="fact-indicator">
          <span class="indicator-text">{currentFactIndex + 1} of {facts.length}</span>
        </div>
        <button class="fact-button next" on:click={nextFact} aria-label="Next fact">
          →
        </button>
      </div>
    {/if}
  {:else}
    <div class="fact-content">
      <p class="fact-text">No facts available</p>
    </div>
  {/if}
</aside>

<style lang="scss">
  @import '../styles/mixins';

  .fun-fact-panel {
    background: linear-gradient(135deg, #3d6e4f 0%, #2d5a3d 100%);
    border: 2px double #52b788;
    border-radius: 2px;
    padding: 1.5rem;
    margin: 2rem 0;
    box-shadow: 
      0 4px 8px rgba(52, 168, 83, 0.2),
      inset 0 1px 0 rgba(255, 255, 255, 0.1);
    position: relative;

    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-image: 
        repeating-linear-gradient(
          0deg,
          rgba(255, 255, 255, 0.02) 0px,
          rgba(255, 255, 255, 0.02) 1px,
          transparent 1px,
          transparent 2px
        );
      pointer-events: none;
      border-radius: 2px;
    }
  }

  .panel-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1.5rem;
  }

  .panel-title {
    font-size: 1.3rem;
    font-weight: 600;
    color: #f5f1e8;
    font-family: 'Georgia', serif;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin: 0;
    font-style: italic;
  }

  .decorative-line {
    flex: 1;
    height: 2px;
    background: linear-gradient(90deg, #81c784 0%, transparent 100%);
  }

  .fact-content {
    padding: 1rem;
    background-color: rgba(245, 241, 232, 0.95);
    border: 1px solid #9f9577;
    border-radius: 1px;
    margin-bottom: 1rem;
  }

  .fact-text {
    font-size: 0.95rem;
    line-height: 1.6;
    color: #1f3a1f;
    font-family: 'Georgia', serif;
    margin: 0 0 0.75rem 0;
    font-weight: 500;
  }

  .fact-source {
    font-size: 0.85rem;
    color: #5a6d52;
    font-style: italic;
    font-family: 'Georgia', serif;
    margin: 0;
  }

  .fact-controls {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 0.5rem;
  }

  .fact-button {
    background-color: rgba(255, 255, 255, 0.15);
    border: 1px solid #81c784;
    color: #f5f1e8;
    font-size: 1.2rem;
    padding: 0.4rem 0.7rem;
    cursor: pointer;
    transition: all 0.2s ease;
    font-family: 'Georgia', serif;
    border-radius: 1px;

    &:hover {
      background-color: #81c784;
      color: #2d5a3d;
      font-weight: bold;
    }

    &:active {
      transform: scale(0.95);
    }
  }

  .prev {
    order: 1;
  }

  .next {
    order: 3;
  }

  .indicator-text {
    color: #f5f1e8;
    font-size: 0.8rem;
    font-family: 'Georgia', serif;
    font-weight: 600;
    letter-spacing: 0.05em;
  }

  .fact-indicator {
    order: 2;
    flex: 1;
    text-align: center;
  }
</style>
