<script>
	import Navbar from './component/Navbar.svelte';
	import Header from './component/Header.svelte';
</script>

<main>
	<Navbar/>
	<Header/>
</main>

<style lang="scss" global>

	:global(body){
		padding: 0;
	}

	main{
		position: relative;
	}

</style>