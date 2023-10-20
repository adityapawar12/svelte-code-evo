<script>
  import { count } from "../store/stores";

  const resetHandler = () => {
    count.set(0);
  };
</script>

<button on:click={resetHandler}>Reset</button>
