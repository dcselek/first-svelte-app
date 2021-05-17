<script>
    import { onMount } from 'svelte'
import { Badge } from 'sveltestrap';

    let data = "";

    onMount(async () => {
       const res = await fetch('https://aws.random.cat/meow');
       data = await res.json();
    });

    
</script>

<svelte:head>
  <title>MEOW</title>
</svelte:head>

<div style="display: flex; align-items: center; flex-direction: column;">
    <div>
        <h1><Badge color="danger">RANDOM CUTE CAT PHOTOS</Badge></h1>
    </div>
    <img style="width: 500px; height: 500px;" alt="" src = {data.file} />
</div>