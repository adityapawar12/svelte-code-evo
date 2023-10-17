<script>
  import AutoFocus from "./components/this-binding/AutoFocus.svelte";
  import PostList from "./components/http-request/PostList.svelte";
  import TabA from "./components/dynamic-components/TabA.svelte";
  import TabB from "./components/dynamic-components/TabB.svelte";
  import TabC from "./components/dynamic-components/TabC.svelte";
  import Counter, {
    // MODULE CONTEXT
    getTotalCount,
  } from "./components/module-context/Counter.svelte";

  // NORMAL APRROACH
  // let activeTab = "TabA";

  // DYNAMIC APPROACH
  let activeTab = TabA;
</script>

<main>
  <!-- HTTP REQUESTS IN SVELTE -->
  <!-- <PostList /> -->

  <!-- THIS BINDING IN SVELTE -->
  <AutoFocus />

  <!-- DYNAMIC COMPONENTS -->
  <!-- NORMAL APRROACH -->
  <!-- <button on:click={() => (activeTab = "TabA")}>Tab A</button>
  <button on:click={() => (activeTab = "TabB")}>Tab B</button>
  <button on:click={() => (activeTab = "TabC")}>Tab C</button>

  {#if activeTab === "TabA"}
    <TabA />
  {/if}
  {#if activeTab === "TabB"}
    <TabB />
  {/if}
  {#if activeTab === "TabC"}
    <TabC />
  {/if} -->

  <!-- DYNAMIC APPROACH -->
  <button on:click={() => (activeTab = TabA)}>Tab A</button>
  <button on:click={() => (activeTab = TabB)}>Tab B</button>
  <button on:click={() => (activeTab = TabC)}>Tab C</button>

  <svelte:component this={activeTab} />

  <!-- MODULE CONTEXT -->
  <Counter />
  <Counter />
  <Counter />
  <button on:click={() => alert(getTotalCount())}>Show total count</button>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
