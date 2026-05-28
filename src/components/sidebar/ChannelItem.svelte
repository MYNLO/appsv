<script>
  // ChannelItem - Clickable row in sidebar for channels or DMs
  // Props: icon ('#' or '@'), name, isActive, isDm (boolean)
  import Avatar from '../atoms/Avatar.svelte';

  let { 
    icon = '#', 
    name = 'channel-name', 
    isActive = false,
    isDm = false,
    avatarUrl = '',
    onClick = () => {} 
  } = $props();
</script>

<button
  onclick={onClick}
  class="w-full flex items-center gap-3 px-4 py-2 rounded-lg transition-colors duration-150 group"
  class:bg-gray-800={isActive}
  class:text-white={isActive}
  class:text-gray-400={!isActive}
  class:hover\:bg-gray-800={!isActive}
  class:hover\:text-gray-200={!isActive}
>
  <!-- Icon or Avatar -->
  {#if isDm && avatarUrl}
    <Avatar imageUrl={avatarUrl} size="small" />
  {:else}
    <span class="text-xl text-gray-500 font-light">{icon}</span>
  {/if}
  
  <!-- Channel/User Name -->
  <span class="font-medium truncate">{name}</span>
</button>
