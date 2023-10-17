<!-- MODULE CONTEXT SCRIPT -->
<script context="module">
  // MODULE SCRIPT VARIABLE(THIS WILL NOT TRIGGER RE RENDERS ON IT'S VALUE CHANGE)
  let totalCount = 0;

  // FUNCTION THAT WILL ALLOW US TO GET THE VALUE OF THIS VARIABLE IN OTHER COMPONENTS.
  export const getTotalCount = () => {
    return totalCount;
  };
</script>

<script>
  let count = 0;

  const clickHandler = () => {
    count += 1;
    totalCount += 1;
  };
</script>

<!-- COMPONENT RE RENDERS ON CHANGING THIS VARIABLE -->
<h2>
  Count - {count}
</h2>

<!-- COMPONENT DOES NOT RE RENDER ON CHANGING THIS VARIABLE -->
<!-- <h2>
  Total Count - {totalCount}
</h2> -->
<button on:click={clickHandler}>Increment</button>
