<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
</script>

<div>
  <h2>Hej! Popup</h2>
  <button on:click={() => dispatch("close", "Aditya")}>Close Popup</button>
</div>
