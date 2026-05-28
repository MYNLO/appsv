<script>
  // Root App component - handles login vs main app view
  import MainLayout from './components/layouts/MainLayout.svelte';
  import Login from './components/Login.svelte';

  // Fake auth state - will be replaced with PocketBase session check
  let isLoggedIn = $state(false);
</script>

{#if isLoggedIn}
  <MainLayout />
{:else}
  <Login />
{/if}
