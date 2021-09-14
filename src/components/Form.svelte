<script>

    export let title = "";
    export let artist = "";

    $: console.log("Title: ", title)
    $: console.log("Artist: ", artist)

    const onSubmit = (event) => {
        event.preventDefault();
        console.log("Title: " + event.target.title.value)
        console.log("Artist: " + event.target.artist.value)

        let newAlbum = {
            "title": event.target.title.value,
            "artist": event.target.artist.value
        }

        // Fetch with post to add new album to json database

        fetch("http://localhost:3000/albums", {
            method: "post",
            headers: {
                "Content-type": "application/json"
            },
            body: JSON.stringify(newAlbum)
        })
        .then(res => res.json())
        .then(data => console.log("data", data))
        .catch(err => console.log("error", err))

    }
</script>

<style>

</style>

<form on:submit={onSubmit}>
    <h3>Add new album</h3>
    <label for="title">Title:</label><input type="text" id="title" bind:value={title} />
    <label for="artist">Artist:</label><input type="text" id="artist" bind:value={artist} />
    <br />
    <button>Save</button>
</form>