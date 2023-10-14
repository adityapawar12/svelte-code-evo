<script>
  import { setContext } from "svelte";

  // IMPORTING OUR CUSTOM COMPONENT
  import Greet from "./components/component-props/Greet.svelte";
  import ComponentA from "./components/context-comps/ComponentA.svelte";
  import Popup from "./components/component-events/Popup.svelte";
  import Outer from "./components/event-forwarding/Outer.svelte";
  import Button from "./components/event-forwarding/Button.svelte";

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

  // COMPONENT EVENTS
  let showPopupFlag = false;

  const showPopup = () => {
    showPopupFlag = true;
  };

  const hidePopup = (event) => {
    console.log("event detail value >>> ", event.detail);
    showPopupFlag = false;
  };

  // EVENT FORWARDING
  const handleGreetings = () => {
    console.log("Greet inside the app component.");
  };
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

  <!-- COMPONENT EVENTS -->
  <button on:click={showPopup}>Show Popup</button>
  {#if showPopupFlag}
    <Popup on:close={hidePopup} />
  {/if}

  <!-- EVENT FORWARDING -->
  <Outer on:greet={handleGreetings} />

  <!-- DOM EVENT FORWARDING -->
  <Button on:click={() => console.log("Button click event forwarded.")} />
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
