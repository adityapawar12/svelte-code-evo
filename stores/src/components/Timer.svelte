<script>
  import { time, elapsedTime } from "../store/stores";

  const dateFormatter = new Intl.DateTimeFormat("en", {
    hour12: true,
    hour: "numeric",
    minute: "2-digit",
    second: "2-digit",
  });
</script>

<h2>The time is {dateFormatter.format($time)}</h2>
<h2>Elapsed time is {$elapsedTime}</h2>
