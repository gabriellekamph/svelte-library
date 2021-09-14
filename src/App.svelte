<script>

	import Home from './components/Home.svelte';
	import Library from './components/Library.svelte';
	import { Router, Link, Route } from "svelte-routing";

	export let url = "";

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

<Router url="{url}">

	<main>
		<h1>Music Library</h1>

		<nav>
			<Link to="/">Home</Link>
			<Link to="library">Library</Link>
		</nav>
	</main>

	<div>
	  <!-- <Route path="blog/:id" component="{BlogPost}" /> -->
	  <Route path="/library" component="{Library}" />
	  <Route path="/" component="{Home}" />
	</div>
	
  </Router>
