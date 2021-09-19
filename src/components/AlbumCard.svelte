<script>

    export let album = {};

</script>

<style>
    .album-card {
        margin: 10px;
        padding: 10px;
        width: 200px;
        height: 230px;
        border: 1px solid #ffc983;
        border-radius: 15px;
        text-align: center;
    }

    img {
        width: 100px;
        margin-bottom: 10px;
        border-radius: 15px;
    }

    p {
        font-size: 12px;
        color: #000;
        text-decoration: none;
    }

    p:hover {
        color: #6d6e71;
        text-decoration: none;
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

<div class="album-card">
    
    <p>{album.title} <br />
    <b>{album.artist}</b>
    </p>
    <img src={album.image} alt="Album cover"/>
    <br />

    {#if album.rented === true}
        <span class="dot-red"></span>
    {:else}
        <span class="dot-green"></span>
    {/if}

</div>

