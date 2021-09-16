<script>

    import { Link } from 'svelte-routing';
    export let params = {};
    export let library = {};

    $: thisAlbum = library.find(a => a.id == params.id);
    $: console.log(thisAlbum);

</script>

<style>

    div {
        margin-left: 40px;
    }

</style>

<div>
    <h3>Info about selected album</h3>

    <p>Id: {thisAlbum.id}</p> <br />
    <p>Title: {thisAlbum.title}</p> <br />
    <p>Artist: {thisAlbum.artist}</p> <br />
    <img src={thisAlbum.image} alt="Album cover"/>

    <br /> <br />

    <Link to="/library">
        <i class="fa fa-arrow-left" aria-hidden="true"></i>
    </Link>
</div>