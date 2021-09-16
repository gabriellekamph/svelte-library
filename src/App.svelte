<script>

	import Home from './components/Home.svelte';
	import Library from './components/Library.svelte';
	import { Router, Link, Route } from "svelte-routing";
	import AlbumDetails from './components/AlbumDetails.svelte';
	import { onMount } from 'svelte';

	export let url = "";
	export let library = [];


	onMount(() => (
		fetch('http://localhost:3000/albums')
		.then(res => res.json())
		.then(data => (
			console.log(data),
			library = data
		))
))

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

	nav {
		text-transform: uppercase;
	}

</style>



<Router url="{url}">

	<main>
		<h1>Music Library</h1>

		<nav>
			<Link to="/">Home</Link> | 
			<Link to="library">Library</Link>
		</nav>
	</main>

	{#each library as album}

	<div>
		<Route path="/library/:id" let:params>
		  <AlbumDetails {library} {album} {params} />
		  </Route>
		<Route path="/library" component="{Library}" />
		<Route path="/" component="{Home}" />
	  </div>

    {/each}


  </Router>
