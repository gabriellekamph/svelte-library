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
        width: 200px;
        height: 230px;
        border: 1px solid #ffc983;
        border-radius: 15px;
        text-align: center;
    }

    img {
        width: 100px;
        margin: 0px;
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


</style>

<div class="album-card">
    
    <p>{album.title} <br />
    <b>{album.artist}</b>
    </p>
    <img src={album.image} alt="Album cover"/>

    <p class="status">{status}</p>

</div>

