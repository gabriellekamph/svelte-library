<script>

    export let album = {};

    let status;

    if (album.rented === true) {
        status = "Not available"

    } else {
        status = "Available"
    }

</script>

<style>
    .album-card {
        margin: 10px;
        padding: 10px;
        width: 300px;
        border: 1px solid rgb(36, 100, 95);
        border-radius: 15px;
        text-align: center;
    }

    img {
        width: 200px;
        margin: 10px;
    }
</style>

<div class="album-card">
    
    <h3>{album.title} <br />
        {album.artist} 
    </h3>
    <img src={album.image} alt="Album cover"/>

    <p class="status">{status}</p>

</div>

