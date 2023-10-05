<script>
  const name = "Freqs";
  const channel = "<b>freq808</b>";
  const hack = `<a href='#' onclick="return alert('you have been hacked!')">Win the Price</a>`;
  const headingId = "heading";
  const id = "heading2";
  const disabled = true;
  const status = "success";
  const isPromoted = true;
  const promoted = true;
</script>

<main>
  <h1>Hello {name}</h1>
  <h2>{@html channel}</h2>
  <h2>{@html hack}</h2>
  <h2 id={headingId}>This is a heading with id</h2>
  <h2 {id}>This is a heading with id shorthand</h2>
  <button disabled={!disabled}>Not Disabled button</button>
  <button {disabled}>Disabled button</button>
  <h2 class="underline">Underlined text</h2>
  <h3 class={status}>Status</h3>
  <h3 class={isPromoted ? "promoted" : ""}>Italic Text</h3>
  <h3 class:promoted={isPromoted}>Italic Text with svelte class directive</h3>
  <h3 class:promoted>Italic Text with svelte class directive shorthand</h3>
</main>

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
