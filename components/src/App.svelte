<script>
  import { setContext } from "svelte";

  // IMPORTING OUR CUSTOM COMPONENT
  import Greet from "./components/Greet.svelte";
  import ComponentA from "./components/context-comps/ComponentA.svelte";

  // VALUES FOR PROPS
  const name = "Aditya";
  const channel = "freq808";

  // OBJECT AS A VALUE FOR A PROP
  const flashTheBoy = {
    name: "Barry",
    heroName: "Flaash",
  };

  // CONTEXT API
  const userName = "Aditya Pawar";

  setContext("username-context", userName);
</script>

<main>
  <!-- CALLING COMPONENTS WITH PROPS -->
  <Greet name={`Bruce`} heroName={`Batmaan`} />
  <Greet name={`Clark`} heroName={`Supermaan`} />
  <Greet name={`Diana`} heroName={`Wonda Woma`} />

  <!-- CALLING COMPONENTS WITH VARIABLES PASSED AS PROPS -->
  <Greet {name} heroName={channel} />
  <Greet {name} />

  <!-- CALLING COMPONENTS WITH OBJECT AS PROPS -->
  <Greet {...flashTheBoy} />

  <!-- CONTEXT API -->
  <h3>{`User Name in App : ${userName}`}</h3>

  <ComponentA />
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
</style>
