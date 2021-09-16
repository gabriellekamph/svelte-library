<script>

	import Library from './components/Library.svelte';
	import { Router, Route } from "svelte-routing";
	import AlbumDetails from './components/AlbumDetails.svelte';
	import { beforeUpdate, afterUpdate, onMount } from 'svelte';
	import Form from './components/Form.svelte';
	
	let record = 'images/record.png';

	export let url = "";
	export let library = [];

	let updateBorrowedStatus;
	$: console.log(updateBorrowedStatus);

	onMount(() => {
		fetch('http://localhost:3000/albums')
		.then(res => res.json())
		.then(data => {
			console.log(data);
			library = data;
		})
	});

	beforeUpdate(() => {
        if (updateBorrowedStatus === true) {
            fetch('http://localhost:3000/albums')
            .then(res => res.json())
            .then(data => {
                library = data;
            })
        }
    });

	afterUpdate(() => {
		updateBorrowedStatus = false;
	});

	const rented = (id) => {
		let albumId = parseInt(id);

		fetch('http://localhost:3000/albums')
		.then(res => res.json())
		.then(data => {
			let status;

			data.forEach(album => {
				if (album.id === albumId) {
					if (album.rented === false) {
						status = true;
					} else {
						status = false;
					};
				};
			});

			fetch('http://localhost:3000/albums/'+ albumId, {
				method: 'PATCH',
				body: JSON.stringify({
					rented: status
				}),
				headers: {
					'Content-type': 'application/json'
				}
			})
			.then(res => res.json())
			.then(data => {
				console.log(data);
				updateBorrowedStatus = true;
			});
		});
	};

</script>

<style>
	main {
		text-align: center;
		margin: 0 auto;
		margin-bottom: 50px;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-around;
		align-items: center;
	}

	h1 {
		color: #6d6e71;
		text-transform: uppercase;
		font-size: 5em;
		font-weight: 200;
	}

	img {
		margin-right: 0px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<Router url="{url}">
	<main>
		<img src={record} width="150px" alt="" />
		<h1>Music Library</h1>
		<Form />
	</main>

	{#each library as album}
		<div>
			<Route path="/library/:id" let:params>
				<AlbumDetails {library} {album} {params} {rented} />
			</Route>
			<Route path="/" component="{Library}" />
	  	</div>
    {/each}
</Router>