<script>
  // MainLayout - Assembles Sidebar + ChatArea into full app layout
  import Sidebar from '../sidebar/Sidebar.svelte';
  import ChatArea from '../chat/ChatArea.svelte';

  let activeChannel = $state(null);

  function handleChannelSelect(channel) {
    activeChannel = channel;
    console.log('Selected:', channel);
  }
</script>

<div class="flex h-screen bg-gray-950">
  <!-- Left Sidebar -->
  <Sidebar onChannelSelect={handleChannelSelect} />

  <!-- Right Chat Area -->
  <ChatArea activeChannel={activeChannel} />
</div>
