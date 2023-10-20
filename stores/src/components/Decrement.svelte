<script>
  import { count } from "../store/stores";

  const decrementHandler = () => {
    count.update((value) => {
      return value - 1;
    });
  };
</script>

<button on:click={decrementHandler}>Decrement</button>
