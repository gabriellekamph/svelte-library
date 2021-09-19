<script>
    import { Link } from 'svelte-routing';
    export let params = {};
    export let library = {};
    export let rented;
    let src;

    $: thisAlbum = library.find(a => a.id == params.id);
    $: console.log(thisAlbum);

    const handleBorrowAlbum = (e) => {
        rented(e.target.id);
    };

    // Fetch to get correct image

    fetch('http://localhost:3000/albums')
        .then(res => res.json())
        .then(data => {
            console.log(data);
            const getCorrectImg = data.map(function(pic) {
                if (params.id == pic.id) {
                    console.log(pic.id);
                    src = `/${pic.image}`;
                }
            })
        })
</script>

<style>
    div {
        margin-left: 40px;
        text-align: center;
    }

    .rented {
        color: red;
    }

    .not-rented {
        color: green;
    }

    i {
        font-size: 20px;
        color: #ffc477;

    }

    img {
        margin: 20px;
    }

    .dot-green {
        height: 10px;
        width: 10px;
        background-color: green;
        border-radius: 50%;
        display: inline-block;
    }

    .dot-red {
        height: 10px;
        width: 10px;
        background-color: rgb(255, 0, 0);
        border-radius: 50%;
        display: inline-block;
    }
</style>

<div>
    <h2>{thisAlbum.title}</h2>
    <p>
        <b>Artist: </b>{thisAlbum.artist} <br />
        <img {src} alt="" width="250px" />
    </p>

    {#if thisAlbum.rented === false}
        <span class="dot-green"></span>
        <p class="not-rented">Album available</p>
        <button on:click={handleBorrowAlbum} id={thisAlbum.id}>Borrow album</button>
    {:else}
        <span class="dot-red"></span>
        <p class="rented">Album rented</p>
        <button on:click="{handleBorrowAlbum}" id={thisAlbum.id}>Return album</button>
    {/if}

    <br /><br />

    <Link to="/">
        <i class="fa fa-arrow-left" aria-hidden="true"></i>
    </Link>
</div>