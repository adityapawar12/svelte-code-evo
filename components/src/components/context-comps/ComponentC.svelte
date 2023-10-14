<script>
  import { getContext } from "svelte";

  const userName = getContext("username-context");
</script>

<div>
  <h2>Component C</h2>
  <h3>User Name in component c : {userName}</h3>
</div>
