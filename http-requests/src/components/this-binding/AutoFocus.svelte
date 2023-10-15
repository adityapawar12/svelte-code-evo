<script>
  import { onMount } from "svelte";

  let inputRef;

  onMount(() => {
    inputRef.focus();
  });
</script>

<div>
  <input type="text" bind:this={inputRef} />
</div>
