<script>
  // Input component - reusable styled text input
  // Props: type, placeholder, value, onInput
  let { type = 'text', placeholder = '', value = '', onInput = () => {} } = $props();
</script>

<input
  type={type}
  placeholder={placeholder}
  value={value}
  oninput={onInput}
  class="w-full px-4 py-2 bg-gray-800 border border-gray-700 rounded-lg text-gray-100 placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent transition-all duration-200"
/>
