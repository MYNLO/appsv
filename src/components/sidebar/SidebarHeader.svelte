<script>
  // SidebarHeader - Logo and app name at top of sidebar
  // Admin-only button to create new channels (manually in PocketBase for V1)
  import Button from '../atoms/Button.svelte';

  let { showCreateChannel = false } = $props();
</script>

<div class="p-4 border-b border-gray-700">
  <!-- App Logo/Name -->
  <div class="flex items-center gap-3 mb-4">
    <div class="w-10 h-10 bg-purple-600 rounded-xl flex items-center justify-center">
      <span class="text-white font-bold text-lg">#</span>
    </div>
    <h1 class="text-xl font-bold text-white">Vibecoding Chat</h1>
  </div>

  <!-- Create Channel Button (Admin Only) -->
  {#if showCreateChannel}
    <Button 
      variant="secondary" 
      label="+ New Channel"
      onClick={() => console.log('Open create channel modal')}
    />
  {/if}
</div>
