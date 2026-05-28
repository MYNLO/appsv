<script>
  // Avatar component - displays a circular image with configurable size
  // Props: imageUrl (string), size ('small' | 'medium' | 'large')
  let { imageUrl = 'https://i.pravatar.cc/150?img=1', size = 'medium' } = $props();

  const sizeClasses = {
    small: 'w-8 h-8',
    medium: 'w-10 h-10',
    large: 'w-16 h-16'
  };
</script>

<div 
  class="rounded-full overflow-hidden bg-gray-700 flex-shrink-0"
  class:{sizeClasses[size]}
>
  <img 
    src={imageUrl} 
    alt="User avatar"
    class="w-full h-full object-cover"
  />
</div>
