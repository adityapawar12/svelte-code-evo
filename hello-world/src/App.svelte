<!-- SCRIPT SECTION IN SVELTE FILE FOR LOGIC -->
<script>
  // BASIC TEXT BINDING
  const name = "Freqs";

  // BASIC HTML BINDING
  const channel = "<b>freq808</b>";
  const hack = `<a href='#' onclick="return alert('you have been hacked!')">Win the Price</a>`;

  // BASIC ATTRIBUTE BINDING
  const headingId = "heading";
  const id = "heading2";
  const disabled = true;
  const status = "success";

  // BASIC CLASS BINDING
  const isPromoted = true;
  const promoted = true;

  // BASIC CONDITIONAL RENDERING
  const num = 0;

  // BASIC LIST RENDERING
  const names = ["Bruce", "Clark", "Diana"];
  const fullNames = [
    { first: "Bruce", last: "Wayne" },
    { first: "Clark", last: "Kent" },
    { first: "Princess", last: "Diana" },
  ];

  // BASIC EVENT HANDLING
  let count = 0;

  const handleClick = (event) => {
    console.log("event >>> ", event);
    count += 1;
  };

  const handleClickWithStepsize = (event, stepSize) => {
    console.log("event >>> ", event);
    count += stepSize;
  };
</script>

<!-- MARKUP/HTML SECTION IN SVELTE FILE FOR HTML TO RENDER -->
<main>
  <!-- BASIC TEXT BINDING -->
  <h1>Hello {name}</h1>

  <!-- BASIC HTML BINDING -->
  <h2>{@html channel}</h2>
  <h2>{@html hack}</h2>

  <!-- BASIC ATTRIBUTE BINDING -->
  <h2 id={headingId}>This is a heading with id</h2>
  <!-- SHORTHAND -->
  <h2 {id}>This is a heading with id shorthand</h2>
  <!-- BOOLEAN -->
  <button disabled={!disabled}>Not Disabled button</button>
  <button {disabled}>Disabled button</button>

  <!-- BASIC CLASS BINDING -->
  <!-- STATIC -->
  <h2 class="underline">Underlined text</h2>
  <!-- DYNAMIC -->
  <h3 class={status}>Status</h3>
  <!-- CONDITIONAL -->
  <h3 class={isPromoted ? "promoted" : ""}>Italic Text</h3>
  <h3 class:promoted={isPromoted}>Italic Text with svelte class directive</h3>
  <h3 class:promoted>Italic Text with svelte class directive shorthand</h3>

  <!-- BASIC CONDITIONAL RENDERING -->
  {#if num === 0}
    <h2>The number is zero.</h2>
  {:else if num > 0}
    <h2>The number is positive.</h2>
  {:else if num < 0}
    <h2>The number is negative.</h2>
  {:else}
    <h2>Not a number.</h2>
  {/if}

  <!-- BASIC LIST RENDERING -->
  {#each names as name, index}
    <h2>{index + 1} {name}</h2>
  {/each}

  {#each fullNames as fullName, index}
    <h2>{index + 1} {`${fullName.first} ${fullName.last}`}</h2>
  {/each}

  <!-- BASIC LIST RENDERING WITH KEYS [ALWAYS USE KEYS FOR LISTS] -->
  {#each names as name, index (name)}
    <h2>{index + 1} {name}</h2>
  {/each}

  {#each fullNames as fullName, index (fullName.first)}
    <h2>{index + 1} {`${fullName.first} ${fullName.last}`}</h2>
  {/each}

  <!-- BASIC EVENT HANDLING -->
  <button on:click={() => (count = count + 1)}>Count {count + 1}</button>
  <button on:click={handleClick}>Count {count + 1}</button>
  <button on:click={(event) => handleClickWithStepsize(event, 1)}
    >Count {count + 1}</button
  >
  <button on:click={(event) => handleClickWithStepsize(event, 5)}
    >Count {count + 1}</button
  >
  <button on:click={(event) => handleClickWithStepsize(event, 10)}
    >Count {count + 1}</button
  >
</main>

<!-- STYLE SECTION IN SVELTE FILE FOR CSS/STYLING -->
<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  .underline {
    text-decoration: underline;
  }

  .danger {
    color: red;
  }

  .success {
    color: greenyellow;
  }

  .promoted {
    font-style: italic;
  }
</style>
