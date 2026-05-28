<script>
  // Login component - simple email/password login form
  // No registration flow (admin creates users manually in PocketBase)
  import Input from './atoms/Input.svelte';
  import Button from './atoms/Button.svelte';

  let email = $state('');
  let password = $state('');
  let error = $state('');

  function handleSubmit() {
    if (!email || !password) {
      error = 'Please enter both email and password';
      return;
    }
    // TODO: Connect to PocketBase auth later
    console.log('Login attempt:', { email, password });
  }
</script>

<div class="min-h-screen flex items-center justify-center bg-gray-900">
  <div class="w-full max-w-md px-8 py-10 bg-gray-800 rounded-2xl shadow-xl border border-gray-700">
    <!-- Header -->
    <div class="text-center mb-8">
      <h1 class="text-3xl font-bold text-white mb-2">Welcome Back</h1>
      <p class="text-gray-400">Sign in to continue to Vibecoding Chat</p>
    </div>

    <!-- Form -->
    <form onsubmit={(e) => { e.preventDefault(); handleSubmit(); }} class="space-y-6">
      <!-- Error Message -->
      {#if error}
        <div class="p-4 bg-red-500/10 border border-red-500/50 rounded-lg text-red-400 text-sm">
          {error}
        </div>
      {/if}

      <!-- Email Input -->
      <div>
        <label for="email" class="block text-sm font-medium text-gray-300 mb-2">Email</label>
        <Input
          id="email"
          type="email"
          placeholder="you@example.com"
          value={email}
          onInput={(e) => email = e.target.value}
        />
      </div>

      <!-- Password Input -->
      <div>
        <label for="password" class="block text-sm font-medium text-gray-300 mb-2">Password</label>
        <Input
          id="password"
          type="password"
          placeholder="••••••••"
          value={password}
          onInput={(e) => password = e.target.value}
        />
      </div>

      <!-- Submit Button -->
      <Button
        variant="primary"
        label="Sign In"
        onclick={handleSubmit}
      />
    </form>

    <!-- Footer Note -->
    <p class="mt-8 text-center text-xs text-gray-500">
      Don't have an account? Ask the admin to add you manually.
    </p>
  </div>
</div>
