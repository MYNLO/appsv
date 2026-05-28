<script>
  // MessageFeed - Scrollable container for all messages
  import MessageBubble from './MessageBubble.svelte';
  import Avatar from '../atoms/Avatar.svelte';

  let { messages = [] } = $props();

  // Fake data for preview (will be replaced with PocketBase fetch)
  const fakeMessages = [
    {
      id: '1',
      avatarUrl: 'https://i.pravatar.cc/150?img=5',
      username: 'Alice Johnson',
      timestamp: '10:30 AM',
      message: 'Hey everyone! How is the project going?',
      isOwn: false
    },
    {
      id: '2',
      avatarUrl: 'https://i.pravatar.cc/150?img=12',
      username: 'You',
      timestamp: '10:32 AM',
      message: 'Pretty good! Just setting up the UI components.',
      isOwn: true
    },
    {
      id: '3',
      avatarUrl: 'https://i.pravatar.cc/150?img=3',
      username: 'Bob Smith',
      timestamp: '10:35 AM',
      message: 'The design looks clean! Love the dark mode vibe.',
      isOwn: false
    },
    {
      id: '4',
      avatarUrl: 'https://i.pravatar.cc/150?img=9',
      username: 'Carol White',
      timestamp: '10:40 AM',
      message: 'Agreed! When are we connecting PocketBase?',
      isOwn: false
    },
    {
      id: '5',
      avatarUrl: 'https://i.pravatar.cc/150?img=12',
      username: 'You',
      timestamp: '10:42 AM',
      message: 'Next step! After we finish all the static components.',
      isOwn: true
    },
  ];

  $effect(() => {
    // This ensures the component re-renders when messages prop changes
  });
</script>

<div class="flex-1 overflow-y-auto">
  {#each (messages.length > 0 ? messages : fakeMessages) as message (message.id)}
    <MessageBubble 
      avatarUrl={message.avatarUrl}
      username={message.username}
      timestamp={message.timestamp}
      message={message.message}
      isOwn={message.isOwn}
    />
  {/each}
</div>
