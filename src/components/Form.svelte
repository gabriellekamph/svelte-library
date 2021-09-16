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
            "artist": event.target.artist.value,
            "image": "images/placeholder.jpg",
            "rented": false
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

        alert("New album saved");
        event.target.reset();
    }
</script>

<style>

    form {
        text-align: right;
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-end;
    }

    input {
        margin-left: 5px;
        height: 25px;
        border-radius: 8px;
        margin-bottom: 5px;
    }

    button {
        height: 25px;
        border-radius: 8px;
        font-size: 12px;
        padding-top: 2px;
    }

    .addNew {
        width: 85%;
        margin-bottom: 5px;
    }

</style>

<form on:submit={onSubmit}>

    <p class="addNew">Add album: 
        <input type="text" id="title" bind:value={title} placeholder="Title" /> <br />
        <input type="text" id="artist" bind:value={artist} placeholder="Artist" /> <br />
        <button>Save</button>
    </p>


</form>