<script>

    import { Link } from 'svelte-routing';
    export let params = {};
    export let library = {};
    export let rented;

    $: thisAlbum = library.find(a => a.id == params.id);
    $: console.log(thisAlbum);

    const handleBorrowAlbum = (e) => {
        rented(e.target.id);
    };

</script>

<style>

    div {
        margin-left: 40px;
    }

    .rented {
        color: red;
    }

    .not-rented {
        color: green;
    }

</style>

<div>
    <h3>Info about selected album</h3>
    <p>
        {thisAlbum.id} <br />
        {thisAlbum.title} <br />
        {thisAlbum.artist} <br />
    </p>

    <!-- <img src={thisAlbum.image} alt="Album cover"/> -->

    <br /><br />

    {#if thisAlbum.rented === false}
        <p class="not-rented">Album available</p>
        <button on:click={handleBorrowAlbum} id={thisAlbum.id}>Borrow album</button>
    {:else}
        <p class="rented">Album rented</p>
        <button on:click="{handleBorrowAlbum}" id={thisAlbum.id}>Return album</button>
    {/if}

    <br />

    <Link to="/library">
        <i class="fa fa-arrow-left" aria-hidden="true"></i>
    </Link>
</div>