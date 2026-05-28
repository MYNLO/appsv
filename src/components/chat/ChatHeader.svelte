<script>
  // ChatHeader - Top bar showing current channel/DM name
  let { title = '#general', isDm = false, avatarUrl = '' } = $props();
</script>

<div class="h-16 px-6 flex items-center justify-between border-b border-gray-700 bg-gray-900">
  <div class="flex items-center gap-3">
    <!-- Icon/Avatar -->
    {#if isDm && avatarUrl}
      <img src={avatarUrl} alt="" class="w-8 h-8 rounded-full" />
    {:else}
      <span class="text-2xl text-gray-500 font-light">#</span>
    {/if}
    
    <!-- Title -->
    <h2 class="text-lg font-semibold text-white">{title}</h2>
  </div>

  <!-- Optional: Channel info button (can be expanded later) -->
  <button class="text-gray-500 hover:text-gray-300 transition-colors" aria-label="Channel info">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <circle cx="12" cy="12" r="10"/>
      <path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/>
      <line x1="12" y1="17" x2="12.01" y2="17"/>
    </svg>
  </button>
</div>
