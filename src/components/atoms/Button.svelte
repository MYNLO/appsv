<script>
  // Button component - reusable styled button
  // Props: variant ('primary' | 'secondary'), onClick
  // Can use label prop OR children content via render
  let { variant = 'primary', label = '', onClick = () => {} } = $props();

  const variantClasses = {
    primary: 'bg-purple-600 hover:bg-purple-700 text-white',
    secondary: 'bg-gray-700 hover:bg-gray-600 text-gray-200'
  };
</script>

<button
  onclick={onClick}
  class="px-4 py-2 rounded-lg font-medium transition-colors duration-200 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2 focus:ring-offset-gray-900 flex items-center justify-center gap-2"
  class:{variantClasses[variant]}
>
  {#if label}
    {label}
  {:else}
    {@render children()}
  {/if}
</button>
