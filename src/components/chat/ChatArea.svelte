<script>
  // ChatArea - Main container for chat window (header + messages + input)
  import ChatHeader from './ChatHeader.svelte';
  import MessageFeed from './MessageFeed.svelte';
  import MessageInput from './MessageInput.svelte';

  let { activeChannel = null } = $props();

  // Determine if viewing a DM or channel
  const isDm = $derived(activeChannel?.isDm ?? false);
  const title = $derived(isDm ? activeChannel?.name : `#${activeChannel?.name ?? 'general'}`);
  const avatarUrl = $derived(activeChannel?.avatar ?? '');
</script>

<div class="flex-1 flex flex-col h-full bg-gray-950">
  <!-- Header -->
  <ChatHeader title={title} isDm={isDm} avatarUrl={avatarUrl} />

  <!-- Messages -->
  <MessageFeed messages={[]} />

  <!-- Input -->
  <MessageInput />
</div>
