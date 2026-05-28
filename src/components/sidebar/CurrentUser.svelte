<script>
  // CurrentUser - Bottom section showing logged-in user info and logout button
  import Avatar from '../atoms/Avatar.svelte';
  import Button from '../atoms/Button.svelte';

  // Fake data - will be replaced with real user from PocketBase
  let currentUser = $state({
    name: 'John Doe',
    email: 'john@example.com',
    avatar: 'https://i.pravatar.cc/150?img=12'
  });

  function handleLogout() {
    console.log('Logging out...');
  }
</script>

<div class="p-4 border-t border-gray-700 bg-gray-800/50">
  <div class="flex items-center gap-3">
    <!-- User Avatar -->
    <Avatar imageUrl={currentUser.avatar} size="medium" />
    
    <!-- User Info -->
    <div class="flex-1 min-w-0">
      <p class="text-sm font-medium text-white truncate">{currentUser.name}</p>
      <p class="text-xs text-gray-500 truncate">{currentUser.email}</p>
    </div>

    <!-- Logout Button -->
    <Button 
      variant="secondary"
      label="Logout"
      onClick={handleLogout}
    />
  </div>
</div>
