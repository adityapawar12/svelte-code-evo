<script>
  import { setContext } from "svelte";

  // IMPORTING OUR CUSTOM COMPONENT
  import Greet from "./components/component-props/Greet.svelte";
  import ComponentA from "./components/context-comps/ComponentA.svelte";
  import Popup from "./components/component-events/Popup.svelte";
  import Outer from "./components/event-forwarding/Outer.svelte";
  import Button from "./components/event-forwarding/Button.svelte";
  import Card from "./components/component-slots/Card.svelte";
  import NameList from "./components/component-slots/NameList.svelte";
  import ChildStyles from "./components/component-styling/ChildStyles.svelte";

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

  <!-- COMPONENT SLOTS -->
  <!-- <Card content={"card content 1"} />
  <Card content={"card content 2"} /> -->

  <!-- COMPONENTS WITH SLOT -->
  <!-- <Card><p>card content</p></Card>
  <Card><h2>card content</h2></Card>
  <Card><img src="https://picsum.photos/200" alt /></Card> -->

  <!-- COMPONENTS WITH DEFAULT SLOT CONTENT -->
  <!-- <Card /> -->

  <!-- COMPONENTS WITH MULTIPLE/NAMED SLOT CONTENT -->
  <Card>
    <div slot="header">
      <h3>Header</h3>
    </div>
    <div slot="content">
      <img src="https://picsum.photos/200" alt />
    </div>
    <!-- <div slot="footer">
      <button>View details</button>
    </div> -->
  </Card>

  <!-- COMPONENT SLOT WITH PROPS -->
  <NameList>
    <h3 slot="hero" let:firstName let:lastName>
      {firstName}
      {lastName}
    </h3>
  </NameList>

  <NameList>
    <h3 slot="hero" let:firstName let:lastName>
      {lastName}
      {firstName}
    </h3>
  </NameList>

  <NameList>
    <h3 slot="hero" let:firstName let:lastName>
      {lastName}
    </h3>
  </NameList>

  <!-- COMPONENT STYLES -->
  <h5>App component global styles.</h5>
  <h4>App component text.</h4>
  <ChildStyles />
</main>

<style>
  :global(h5) {
    color: violet;
  }

  h4 {
    color: orange;
  }

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
