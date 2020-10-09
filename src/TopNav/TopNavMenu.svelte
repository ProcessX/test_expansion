<script>
    // your script goes here
    import DropdownMenu from './DropdownMenu.svelte';

    export let menuOpen;
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


    .topNav__menu{
        position: absolute;
        left: 0;
        width: 100%;
        background-color: $green-cream;
        z-index: 0;
        padding: 1rem;
        top: 100%;


        @include for-size(smallerThanDesktop){
            transform: translateY(-100%);

            &--open{
                transform: translateY(0);
            }
        }

        @include for-size(tablet){
        }

        @include for-size(desktop){
            position: relative;
            display: flex;
            flex-direction: row-reverse;
            align-items: center;
            padding: 0 50px;
            box-sizing: border-box;
            z-index: 1000;
            background-color: transparent;
        }
    }

    .menu__tab__li{
        list-style: none;
        padding: 0;
        margin: 0 0 4rem 0;

        @include for-size(desktop){
            display: flex;
            flex-direction: row-reverse;
            margin: 0;
        }
    }

    .menu__tab__el{
        margin: 0 0 1rem 0;

        @include for-size(desktop){
            margin: 0;
        }
    }

    .menu__tab{
        color: black;
        text-decoration: none;

        &--bold{
            font-weight: bold;
        }
    }

    .dropdownMenu__li{
        list-style: none;
        padding: 0;
        margin: 0;

        @include for-size(desktop){
            display: flex;
            flex-direction: row-reverse;
        }
    }

    .dropdownMenu__el{
        margin: 0 0 2rem 0;

        &:last-child{
            margin-bottom: 0;
        }

        @include for-size(desktop){
            margin: 0;
        }
    }
</style>

<!-- markup (zero or more items) goes here -->
<div class="topNav__menu {menuOpen ? 'topNav__menu--open' : ''}">
    <ul class="menu__tab__li">
        <li class="menu__tab__el">
            <a href="#" class="menu__tab">Se connecter</a>
        </li>
        <li class="menu__tab__el">
            <a href="#" class="menu__tab">Contact</a>
        </li>
    </ul>

    <ul class="menu__tab__li">
        <li class="menu__tab__el">
            <a href="#" class="menu__tab menu__tab--bold">Je suis</a>
        </li>
        <li class="menu__tab__el">
            <a href="#" class="menu__tab menu__tab--bold">Je trouve</a>
        </li>
    </ul>

    <ul class="dropdownMenu__li">
        <li class="dropdownMenu__el">
            <DropdownMenu title={'Ma ville'}/>
        </li>
        <li class="dropdownMenu__el">
            <DropdownMenu title={'Vivre à Binche'}/>
        </li>
        <li class="dropdownMenu__el">
            <DropdownMenu title={'Que faire à Binche'}/>
        </li>
    </ul>
</div>