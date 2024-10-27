<script>
  export let title = '';
  export let level = 1; // Default to h1
  export let className = '';
</script>

{#if level === 1}
  <h1 class={className}>
    {title}
  </h1>
{:else if level === 2}
  <h2 class={className}>
    {title}
  </h2>
{:else if level === 3}
  <h3 class={className}>
    {title}
  </h3>
{:else if level === 4}
  <h4 class={className}>
    {title}
  </h4>
{:else if level === 5}
  <h5 class={className}>
    {title}
  </h5>
{:else if level === 6}
  <h6 class={className}>
    {title}
  </h6>
{/if}
