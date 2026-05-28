<script>
  // MessageBubble - Single message with avatar, username, timestamp, and text
  import Avatar from '../atoms/Avatar.svelte';

  let {
    avatarUrl = 'https://i.pravatar.cc/150?img=1',
    username = 'Username',
    timestamp = '10:30 AM',
    message = 'This is a message',
    isOwn = false
  } = $props();
</script>

<div class="flex gap-4 px-6 py-3 hover:bg-gray-800/30 transition-colors">
  <!-- Avatar -->
  <Avatar imageUrl={avatarUrl} size="medium" />

  <!-- Message Content -->
  <div class="flex-1 min-w-0">
    <!-- Username and Timestamp Row -->
    <div class="flex items-baseline gap-2 mb-1">
      <span class="font-semibold text-white">{username}</span>
      <span class="text-xs text-gray-500">{timestamp}</span>
    </div>

    <!-- Message Text -->
    {#if isOwn}
      <p class="text-sm leading-relaxed text-gray-200">
        {message}
      </p>
    {:else}
      <p class="text-sm leading-relaxed text-gray-300">
        {message}
      </p>
    {/if}
  </div>
</div>
