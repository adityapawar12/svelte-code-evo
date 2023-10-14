<script>
  // NORMAL APPROACH
  let firstName = "bruce";
  let lastName = "wayne";

  // REACTIVE APPROACH (REACTIVE DECLARATION)
  $: fullName = `${firstName} ${lastName}`;

  let items = [
    { id: 1, title: "TV", price: 50000 },
    { id: 2, title: "Phone", price: 30000 },
    { id: 3, title: "Laptop", price: 40000 },
  ];

  $: total = items.reduce((total, curr) => (total = total + curr.price), 0);

  // REACTIVE APPROACH (REACTIVE STATEMENTS)
  // SINGLE LINE
  $: console.log(`Full Name is [single line] : ${firstName} ${lastName}`);

  // MULTIPLE LINE
  $: {
    const greet = `Full Name is [multiple line] : ${firstName} ${lastName}`;
    console.log(greet);
  }

  let volume = 0;

  $: if (volume < 0) {
    alert("Volume cannot be lesser that 0");
    volume = 0;
  } else if (volume > 20) {
    alert("Volume cannot be greater than 20");
    volume = 20;
  }
</script>

<main>
  <!-- NORMAL APPROACH -->
  <h2>{firstName} {lastName}!</h2>

  <!-- REACTIVE APPROACH (REACTIVE DECLARATION) -->

  <button
    on:click={() => {
      firstName = "clark";
      lastName = "kent";
    }}>Change hero</button
  >

  <h2>{fullName}</h2>

  <!--  TOTAL VALUE WON'T CHANGE BECAUSE WE HAVE NOT REASSIGNED THE VALUE TO ITEMS ARRAY -->
  <button on:click={() => items.push({ id: 4, title: "Keyboard", price: 2000 })}
    >Add Item That doesn't work</button
  >

  <!--  TOTAL VALUE WILL CHANGE BECAUSE WE HAVE REASSIGNED THE VALUE TO ITEMS ARRAY -->
  <button
    on:click={() =>
      (items = [...items, { id: 4, title: "Keyboard", price: 2000 }])}
    >Add Item That works</button
  >

  <h3>
    Total : {total}
  </h3>

  <h3>{volume}</h3>

  <div>
    <button on:click={() => (volume += 2)}>Increase Volume</button>
    <button on:click={() => (volume -= 2)}>Decrease Volume</button>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h2 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
