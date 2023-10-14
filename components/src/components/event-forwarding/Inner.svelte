<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  const greet = () => {
    dispatch("greet", "ADITYA");
  };
</script>

<div>
  Inner Component

  <!-- EVENT FORWARDING -->
  <button on:click={greet}>Greetings from inner component</button>
</div>
