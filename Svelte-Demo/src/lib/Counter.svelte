<script>
  let count = 0;
  const increment = () => {
    count += 1;
  };
  const double = () => {
    count *= 2;
  };
</script>

{#if count < 5}
  <button on:click={increment}>
    count is {count}
  </button>
{:else}
  <button on:click={double}>
    count is {count}
  </button>
{/if}
