<script>
  import { Button } from "sveltestrap";

  export let kind;
</script>

<Button {...$$restProps} class={`mb-${kind}`}> Click {kind} </Button>

<style>
    :global(.mb-meow){
        width: 120px;
        background-color: blue;
    }
</style>