<script>
  import { count } from "../store/stores";

  const incrementHandler = () => {
    count.update((value) => {
      return value + 1;
    });
  };
</script>

<button on:click={incrementHandler}>Increment</button>
