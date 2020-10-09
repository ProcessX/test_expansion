<script>
    // your script goes here
    import TopNavMenu from './TopNavMenu.svelte';

    function toggleBurger(){
        console.log('toggleBurger');
    }
</script>

<style type="text/scss">
    /* your styles go here */
    $green-cream: #C1DFC4;
    $orange: #EA5B0C;

    .topNav{
        display: grid;
        width: 100%;
        box-sizing: border-box;
        background-color: $green-cream;
        position: fixed;
        top: 0;
        left: 0;
        padding: 1rem;
    }

    .topNav__logo{
        grid-column-start: 1;
        justify-self: start;
    }

    .topNav__burger{
        grid-column-start: 2;
        justify-self: end;
    }
</style>

<!-- markup (zero or more items) goes here -->
<nav class="topNav">
    <a class="topNav__logo" href="#">Logo</a>

    <TopNavMenu/>

    <a class="topNav__burger" href="#" on:click={toggleBurger}>Burger</a>
</nav>