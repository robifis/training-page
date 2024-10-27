<script>
	import '../app.css';
	import MainNav from '../lib/MainNav.svelte';
	let { children } = $props();
</script>

<style>
  :global(body) {
    @apply bg-gray-900 text-white font-sans;
  }
  .container {
    @apply max-w-4xl mx-auto p-4;
  }
  h1 {
    @apply text-3xl font-bold text-purple-500 mb-4;
  }
  h2 {
    @apply text-2xl font-semibold text-purple-400 mb-3;
  }
  h3 {
    @apply text-xl font-medium text-purple-300 mb-2;
  }
  a {
    @apply text-purple-500 hover:text-purple-400 transition-colors;
  }
  nav {
    @apply flex justify-center gap-4 p-4 bg-gray-800;
  }
  .menu-item {
    @apply relative;
  }
  .submenu {
    @apply hidden absolute bg-gray-800 p-2 border border-gray-700;
  }
  .menu-item:hover .submenu {
    @apply block;
  }
</style>

<MainNav />
<div class="container">
  {@render children()}
</div>
