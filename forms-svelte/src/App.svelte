<script>
  // OBJECT TO KEEP TRACK OF FORM VALUES(WE CAN ALSO USE STRINGS AND SEPARATE VARIABLES).
  const formValues = {
    name: "",
    profileSummary: "",
    country: "",
    jobLocation: [],
    remoteWork: false,
    skillSet: [],
    yearsOfExperience: "",
  };

  //   // SUBMIT FORM HANDLER FUNCTION
  //   function submitForm(event) {
  //     event.preventDefault();
  //     console.log(formValues);
  //   }

  // SUBMIT FORM HANDLER FUNCTION WITH EVENT MODIFIER
  function submitForm(event) {
    console.log(formValues);
  }
</script>

<main>
  <!-- FORM VALUES LOGGED INTO HTML -->
  <div>
    <p>{JSON.stringify(formValues, null, 2)}</p>
  </div>

  <!-- FORM -->
  <!-- <form on:submit={submitForm}> -->
  <!-- FORM WITH EVENT MODIFIER -->
  <form on:submit|preventDefault={submitForm}>
    <!-- SIMPLE INPUT -->
    <div>
      <label for="name">Name</label>
      <input type="number" id="name" bind:value={formValues.name} />
    </div>

    <!-- TEXTAREA -->
    <div>
      <label for="profileSummary">Profile Summary</label>
      <textarea id="profileSummary" bind:value={formValues.profileSummary} />
    </div>

    <!-- SINGLE VALUE SELECT -->
    <div>
      <label for="country">Country</label>
      <select id="country" bind:value={formValues.country}>
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="vietnam">Vietnam</option>
        <option value="singapore">Singapore</option>
      </select>
    </div>

    <!-- MULTIPLE VALUE SELECT -->
    <div>
      <label for="jobLocation">Job Location</label>
      <select id="jobLocation" bind:value={formValues.jobLocation} multiple>
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="vietnam">Vietnam</option>
        <option value="singapore">Singapore</option>
      </select>
    </div>

    <!-- SINGLE VALUE CHECKBOX -->
    <div>
      <input
        type="checkbox"
        id="remoteWork"
        bind:checked={formValues.remoteWork}
      />
      <label for="remoteWork">Open to remote work?</label>
    </div>

    <!-- MULTIPLE VALUE CHECKBOX -->
    <div>
      <label for="">Skill Set</label>
      <input
        type="checkbox"
        id="html"
        value="html"
        bind:group={formValues.skillSet}
      />
      <label for="html">Html</label>
      <input
        type="checkbox"
        id="css"
        value="css"
        bind:group={formValues.skillSet}
      />
      <label for="css">Css</label>
      <input
        type="checkbox"
        id="javascript"
        value="javascript"
        bind:group={formValues.skillSet}
      />
      <label for="javascript">Javascript</label>
    </div>

    <!-- RADIO BUTTONS -->
    <div>
      <label for="">Year of Experience</label>
      <input
        type="radio"
        id="0-2"
        value="0-2"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="0-2">0-2</label>
      <input
        type="radio"
        id="3-5"
        value="3-5"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="3-5">3-5</label>
      <input
        type="radio"
        id="6-10"
        value="6-10"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="6-10">6-10</label>
      <input
        type="radio"
        id="11-15"
        value="11-15"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="11-15">11-15</label>
    </div>

    <div>
      <!--  SUBMTI BUTTON -->
      <button type="submit">Submit</button>
    </div>
  </form>
</main>

<style>
  input + label {
    display: inline-flex;
  }

  main {
    /* text-align: center; */
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  /* h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  } */

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
