<script>
    import { onMount } from 'svelte'
    import { Badge, Button } from 'sveltestrap';

    let data = "";

    onMount(async () => {
       const res = await fetch('https://aws.random.cat/meow');
       data = await res.json();
    });

    function refresh(){
        history.go(0);
    }    
</script>

<svelte:head>
  <title>MEOW</title>
</svelte:head>

<div style="display: flex; align-items: center; flex-direction: column;">
    <div>
        <h1><Badge color="danger">RANDOM CUTE CAT PHOTOS</Badge></h1>
    </div>
    <img style="width: 500px; height: 500px;" alt="" src = {data.file} />
    <input type="button" style="margin-top: 16px;" on:click={refresh} value="Click & New🐱" />
</div>