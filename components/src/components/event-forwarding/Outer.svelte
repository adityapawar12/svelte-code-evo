<script>
  import Inner from "./Inner.svelte";
</script>

<div>
  Outer Component

  <!-- EVENT FORWARDED TO PARENT -->
  <Inner on:greet />
</div>
