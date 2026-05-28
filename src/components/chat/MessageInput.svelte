<script>
  // MessageInput - Text input area with send button at bottom of chat
  import Button from '../atoms/Button.svelte';

  let message = $state('');

  function handleSend() {
    if (!message.trim()) return;
    
    console.log('Sending message:', message);
    message = ''; // Clear input
  }

  function handleKeyDown(event) {
    // Send on Enter (without Shift)
    if (event.key === 'Enter' && !event.shiftKey) {
      event.preventDefault();
      handleSend();
    }
  }
</script>

<div class="p-6 border-t border-gray-700 bg-gray-900">
  <div class="flex gap-4 items-end">
    <!-- Message Input -->
    <div class="flex-1 relative">
      <textarea
        bind:value={message}
        onkeydown={handleKeyDown}
        placeholder="Type a message..."
        rows={1}
        class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-xl text-gray-100 placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent resize-none transition-all duration-200"
        style="min-height: 48px; max-height: 120px;"
      ></textarea>
    </div>

    <!-- Send Button -->
    <Button 
      variant="primary"
      onclick={handleSend}
    >
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <line x1="22" y1="2" x2="11" y2="13"/>
        <polygon points="22 2 15 22 11 13 2 9 22 2"/>
      </svg>
    </Button>
  </div>

  <!-- Formatting hint -->
  <p class="mt-2 text-xs text-gray-500">
    Press <kbd class="px-1.5 py-0.5 bg-gray-800 rounded text-gray-400">Enter</kbd> to send, <kbd class="px-1.5 py-0.5 bg-gray-800 rounded text-gray-400">Shift+Enter</kbd> for new line
  </p>
</div>
