<script>
    export let title = "";
    export let artist = "";
    export let onSubmit;
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