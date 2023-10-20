<script>
  import { count, customCount } from "../store/stores";
  //   import { onDestroy } from "svelte";

  //   let counter = 0;

  //   const unsubscribe = count.subscribe((value) => {
  //     counter = value;
  //   });

  //   onDestroy(unsubscribe);
</script>

<h2>Current counter value is : {$count}</h2>

<h2>Custom counter value is : {$customCount}</h2>
<div>
  <button
    on:click={() => {
      customCount.increment();
    }}>Increment</button
  >
  <button
    on:click={() => {
      customCount.increment(5);
    }}>Increment 5</button
  >
  <button
    on:click={() => {
      customCount.decrement();
    }}>Decrement</button
  >
  <button
    on:click={() => {
      customCount.decrement(5);
    }}>Decrement 5</button
  >
  <button
    on:click={() => {
      customCount.reset();
    }}>Reset</button
  >
</div>
