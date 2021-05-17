<script>
  import { Badge } from "sveltestrap";
  import { submitWrite } from "../stores/stores";

  let write_value = "";

  const unsubscribe = submitWrite.subscribe((value) => {
    write_value = value;
  });
</script>

<svelte:head>
  <title>Second Page</title>
</svelte:head>

<div>
  {#if write_value === ""}
    <h1>
      You didn't wrote anything at first page. You should go back and write
      anything
    </h1>
  {:else}
    <h1>
      Here is the second page and you had wrote
      <Badge color="danger">
        "{write_value}"
      </Badge>
      that before at first page!
    </h1>
  {/if}
</div>
