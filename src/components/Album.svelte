<script>

    export let album = {};

</script>

<style>

    .album-info {
        margin: 10px;
        padding: 10px;
        width: 300px;
        border: 1px solid rgb(36, 100, 95);
        border-radius: 15px;
    }

    img {
        width: 200px;
        margin: 20px;
    }

</style>

    <div class="album-info">
        {album.title} <br/>
        <b>{album.artist}</b> 
        <br />

        <img src={album.image} alt="Album cover"/>
    </div>

