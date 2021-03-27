<script>
	import List from './List.svelte'
	import Loading from './Loading.svelte';
	import SearchInput from './SearchInput.svelte'
	// import favicon from '../public/favicon.png'
</script>

<main>
	<h1><a href="https://restcountries.eu/" target="_blank">Countries API</a></h1>
	<h2>with <img src="/svelte_logo.png" width="16px" alt=""> Svelte</h2>
	<SearchInput />
	<List />
</main>
<Loading />


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
		margin-block-end: 0.4em;
	}

	h2 {
		margin-bottom: 50px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	a {
		color: inherit;
		text-decoration: none
	}
</style>