<script>
  // SectionTitle - Header text for sidebar sections (e.g., "TEXT CHANNELS", "DIRECT MESSAGES")
  let { label = 'SECTION NAME', showPlus = false } = $props();
</script>

<div class="flex items-center justify-between px-4 py-2 mt-4 mb-1">
  <div class="flex items-center gap-1">
    <span class="text-xs font-semibold text-gray-500 uppercase tracking-wider">{label}</span>
    {#if showPlus}
      <button 
        class="w-4 h-4 flex items-center justify-center text-gray-500 hover:text-gray-300 transition-colors"
        onclick={() => console.log('Add new')}
      >
        +
      </button>
    {/if}
  </div>
</div>
