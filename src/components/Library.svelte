<script>
    import { onMount } from 'svelte';
    import AlbumCard from './AlbumCard.svelte';
    import { Link } from 'svelte-routing';

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
</style>

<div>
    {#each library as album}
        <Link to={`/library/${album.id}`} key={album.id}>
            <AlbumCard {album} />
        </Link>
    {:else}
        <div>Loading albums..</div>
    {/each}
</div>