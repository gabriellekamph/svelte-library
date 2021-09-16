<script>

    export let album = {};

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
        margin: 20px;
    }

    .artist {
        text-transform: uppercase;
        margin-top: 5px;
    }

</style>

<div class="album-card">

    <h3>{album.title}</h3>
    <p class="artist">{album.artist}</p> 

    <img src={album.image} alt="Album cover"/>

</div>

