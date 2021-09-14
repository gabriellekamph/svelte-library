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

    p {
        font-size: 12px;
    }

    h3 {
        font-size: 15px;
        width: 100%;
    }

    form {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        text-align: center;
        margin-bottom: 50px;
    }

    input {
        margin-right: 20px;
    }

</style>

<form on:submit={onSubmit}>
    <h3>Add new album</h3><br />
    <label for="title">Title: <input type="text" id="title" bind:value={title} /></label>
    <label for="artist">Artist: <input type="text" id="artist" bind:value={artist} /></label>
    <br />
    <button>Save</button>
</form>