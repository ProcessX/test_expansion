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
        } @else if $size == desktop {
            @media (min-width: #{$resolution-desktop}) {@content;}
        } @else if $size == smallerThanTablet {
            @media (max-width: #{$resolution-tablet}) {@content;}
        } @else if $size == smallerThanDesktop {
            @media (max-width: #{$resolution-desktop}) {@content;}
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
        position: fixed;
        top: 0;
        left: 0;
        z-index: 1000;

        &--menuOpen{
            //box-shadow: 10px 5px 5px red;
        }

        @include for-size(smallerThanTablet){
            &:before{
                content: "";
                height: 100vh;
                width: 100vw;
                position: absolute;
                top: 0;
                left: 0;
                background-color: black;
                opacity: 0;
                pointer-events: none;
            }

            &--menuOpen{
                &:before{
                    opacity: 0.75;
                    pointer-events: all;
                }

                .topNav__tab__li{
                    -webkit-box-shadow: -1px 3px 13px 7px rgba(0,0,0,0.19);
-moz-box-shadow: -1px 3px 13px 7px rgba(0,0,0,0.19);
box-shadow: -1px 3px 13px 7px rgba(0,0,0,0.19);
                }
            }
        }

        @include for-size(desktop){
            background-color: $green-cream;
        }

    }

    .topNav__tab__li{
        position: relative;
        list-style: none;
        margin: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: $green-cream;
        z-index: 200;
        padding: 0.5rem 1rem;

        @include for-size(smallerThanDesktop){
            width: 100%;
        }

        @include for-size(desktop){
            padding: 0.5rem 50px;
        }
    }

    .topNav__tab__el{}

    .topNav__tab{
        &--logo{
            display: inline-block;
            height: 3rem;
            width: 3rem;
            max-height: 3rem;
            max-width: 3rem;
            overflow: hidden;
            text-indent: 100%;
            background-image: url('/asset/img/logo-binche.png');
            background-size: contain;
            background-repeat: no-repeat;
            background-position: left center;
        }

        &--burger{
            @include for-size(desktop){
                display: none;
            }
        }
    }

</style>

<!-- markup (zero or more items) goes here -->
<nav class="topNav {menuOpen ? "topNav--menuOpen" : ""}">
    <ul class="topNav__tab__li">
        <li class="topNav__tab__el">
            <a class="topNav__tab topNav__tab--logo" href="#">Logo</a>
        </li>
        <li class="topNav__tab__el">
            <a class="topNav__tab topNav__tab--burger" href="#" on:click={toggleBurger}>Burger</a>
        </li>
    </ul>

    <TopNavMenu menuOpen={menuOpen}/>
</nav>