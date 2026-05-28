<script>
  // Sidebar - Main left column container with channels and DMs
  import SidebarHeader from './SidebarHeader.svelte';
  import SectionTitle from './SectionTitle.svelte';
  import ChannelItem from './ChannelItem.svelte';
  import CurrentUser from './CurrentUser.svelte';

  // Props for callbacks
  let { onChannelSelect = () => {} } = $props();

  // Fake data - will be replaced with PocketBase fetch later
  const channels = $state([
    { id: '1', name: 'general', icon: '#' },
    { id: '2', name: 'design', icon: '#' },
    { id: '3', name: 'development', icon: '#' },
    { id: '4', name: 'random', icon: '#' },
  ]);

  const directMessages = $state([
    { id: 'u1', name: 'Alice Johnson', avatar: 'https://i.pravatar.cc/150?img=5' },
    { id: 'u2', name: 'Bob Smith', avatar: 'https://i.pravatar.cc/150?img=3' },
    { id: 'u3', name: 'Carol White', avatar: 'https://i.pravatar.cc/150?img=9' },
  ]);

  let activeChannel = $state(null);

  function handleChannelClick(channel) {
    activeChannel = channel;
    onChannelSelect(channel);
  }

  function handleDmClick(user) {
    activeChannel = { ...user, isDm: true };
    onChannelSelect({ ...user, isDm: true });
  }
</script>

<div class="w-64 bg-gray-900 flex flex-col h-full border-r border-gray-700">
  <!-- Header -->
  <SidebarHeader showCreateChannel={true} />

  <!-- Scrollable Content -->
  <div class="flex-1 overflow-y-auto">
    <!-- Text Channels Section -->
    <SectionTitle label="Text Channels" showPlus={true} />
    {#each channels as channel}
      <ChannelItem 
        icon="#"
        name={channel.name}
        isActive={activeChannel?.id === channel.id && !activeChannel?.isDm}
        onClick={() => handleChannelClick(channel)}
      />
    {/each}

    <!-- Direct Messages Section -->
    <SectionTitle label="Direct Messages" showPlus={true} />
    {#each directMessages as dm}
      <ChannelItem 
        icon="@"
        name={dm.name}
        isDm={true}
        avatarUrl={dm.avatar}
        isActive={activeChannel?.id === dm.id && activeChannel?.isDm}
        onClick={() => handleDmClick(dm)}
      />
    {/each}
  </div>

  <!-- Current User (fixed at bottom) -->
  <CurrentUser />
</div>
