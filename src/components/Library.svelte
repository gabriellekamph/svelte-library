<script>

    import { onMount } from 'svelte';
    import Album from './Album.svelte';
    import Form from './Form.svelte';


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

    div {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }

    .form {
        width: 100%;
    }

</style>

<div>

    <div class="form">
        <Form />
    </div>

    {#each library as album}
    <Album {album} />
    {:else}
    <div>Loading albums..</div>
    {/each}

</div>
