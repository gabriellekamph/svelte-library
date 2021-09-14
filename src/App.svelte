<script>

	import Library from './components/Library.svelte';
	import Form from './components/Form.svelte';
	
</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
	}

	h1 {
		color: rgb(36, 100, 95);
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 200;
		width: 100%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

</style>

<main>
	<h1>Music Library</h1>
	<Form />
	<Library />
</main>