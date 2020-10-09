<script>
    // your script goes here
    import TopNavMenu from './TopNavMenu.svelte';

    let menuOpen = false;

    function toggleBurger(){
        console.log('toggleBurger');
        menuOpen = !menuOpen;
    }

</script>

<style type="text/scss">
    /* your styles go here */
    $resolution-tablet: 768px;
    $resolution-desktop: 998px;

    @mixin for-size($size){
        @if $size == tablet {
            @media (min-width: #{$resolution-tablet}) {@content;}
        } @else if $size == desktop{
            @media (min-width: #{$resolution-desktop}) {@content;}
        }
    }

    $green-cream: #C1DFC4;
    $orange: #EA5B0C;

    .topNav{
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        box-sizing: border-box;
        background-color: $green-cream;
        position: fixed;
        top: 0;
        left: 0;
        padding: 1rem;
        z-index: 1000;

        &--menuOpen{
            //box-shadow: 10px 5px 5px red;
        }
    }

    .topNav__logo{
        grid-column-start: 1;
        height: 3rem;
        width: 3rem;
        max-height: 3rem;
        max-width: 3rem;
        overflow: hidden;
        text-indent: 100%;

        background-color: gray;
    }

    .topNav__burger{
        grid-column-start: 2;

        @include for-size(desktop){
            display: none;
        }
    }
</style>

<!-- markup (zero or more items) goes here -->
<nav class="topNav {menuOpen ? "topNav--menuOpen" : ""}">
    <a class="topNav__logo" href="#">Logo</a>

    <TopNavMenu menuOpen={menuOpen}/>

    <a class="topNav__burger" href="#" on:click={toggleBurger}>Burger</a>
</nav>