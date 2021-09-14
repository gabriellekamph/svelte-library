<script>

    import { onMount } from 'svelte';
    import Album from './Album.svelte';

    export let library = [];

    onMount(() => (
        fetch('http://localhost:3000/albums')
        .then(res => res.json())
        .then(data => (
            console.log(data),
            library = data
        ))
    ))

</script>

<style>

</style>

<div>

    {#each library as album}
    <Album {album} />
    {:else}
    <div>Loading albums..</div>
    {/each}

</div>