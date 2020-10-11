<script>
	import Navbar from './component/Navbar.svelte';
	import Header from './component/Header.svelte';
</script>

<main class="page">
	<Navbar/>
	<Header/>
</main>

<style lang="scss">

	:global(body){
		padding: 0;
	}

	main{
		position: relative;
	}

	:global(body.lockScroll){
		
		overflow: hidden;
		//position: fixed;
	}

</style>