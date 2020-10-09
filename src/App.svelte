<script>
	import TopNav from './TopNav/TopNav.svelte';
	import Header from './Header/Header.svelte';

	export let name;
</script>

<main>
	<TopNav/>
	<Header/>
</main>

<style type="text/scss">
	:global(body){
		padding: 0;
	}

	main{
		position: relative;
	}

</style>