<script>
    // your script goes here
    import DropdownMenu from './DropdownMenu.svelte';

    export let menuOpen;

    let dropdownTabPlaceholder = [
        {
            title: 'Tab01',
            link: '#'
        },
        {
            title: 'Tab02',
            link: '#'
        },
        {
            title: 'Tab03',
            link: '#'
        },
    ];
</script>

<style type="text/scss">
    /* your styles go here */
    $resolution-tablet: 768px;
    $resolution-desktop: 998px;
    $resolution-desktop-large: 1280px; 

    
    @mixin for-size($size){
        @if $size == tablet {
            @media (min-width: #{$resolution-tablet}) {@content;}
        } @else if $size == desktop {
            @media (min-width: #{$resolution-desktop}) {@content;}
        } @else if $size == desktop-large {
            @media (min-width: #{$resolution-desktop-large}) {@content;}
        }@else if $size == smallerThanTablet {
            @media (max-width: #{$resolution-tablet}) {@content;}
        } @else if $size == smallerThanDesktop {
            @media (max-width: #{$resolution-desktop}) {@content;}
        }@else if $size == smallerThanDesktopLarge {
            @media (max-width: #{$resolution-desktop-large}) {@content;}
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
        box-sizing: border-box;
        top: 100%;

        @include for-size(smallerThanDesktopLarge){
            transform: translateY(-100%);
            padding: 2rem 1rem 2rem 1rem;;

            &--open{
                transform: translateY(0);
            }
        }

        @include for-size(tablet){
        }

        @include for-size(desktop-large){
            position: absolute;
            height: 100%;
            top: 0;
            display: grid;
            grid-template-columns: repeat(12,1fr);
            pointer-events: none;
            align-content: center;
            padding: 0 50px;
            box-sizing: border-box;
            z-index: 1000;
            background-color: transparent;

            > * {
                pointer-events: all;
            }
        }
    }


    .menu__tab__li{
        list-style: none;
        position: relative;
        padding: 0;
        margin: 0;

        @include for-size(smallerThanDesktopLarge){
            padding: 2rem 0 2rem 0;

            &:after{
                content: "";
                display: block;
                height: 1px;
                width: 100%;
                background-color: black;
                position: absolute;
                bottom: 0;                   
                left: 0;
            }
        }

        @include for-size(desktop-large){
            display: flex;
            flex-direction: row-reverse;
            grid-row-start: 1;
            align-self: center;
            font-size: 14px;

            &--account{
                grid-column: -1/-3;
            }

            &--personal{
                grid-column: -3/-5;
            }
        }
    }

    .menu__tab__el{
        margin: 0 0 1rem 0;

        @include for-size(desktop-large){
            margin: 0 0 0 2rem;

            &:last-child{
                margin: 0;
            }
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
        padding: 2rem 0 2rem 0;
        margin: 0;

        @include for-size(desktop){
            
        }

        @include for-size(desktop-large){
            padding: 0;
            align-self: center;
            display: flex;
            flex-direction: row-reverse;
            justify-content: center;
            grid-column: 5/9;
            grid-row-start: 1;
        }
    }

    .dropdownMenu__el{
        margin: 0 0 2rem 0;

        &:last-child{
            margin-bottom: 0;
        }

        @include for-size(desktop-large){
            margin: 0 0 0 2rem;
        }
    }
</style>

<!-- markup (zero or more items) goes here -->
<div class="topNav__menu {menuOpen ? 'topNav__menu--open' : ''}">
    <ul class="menu__tab__li menu__tab__li--account">
        <li class="menu__tab__el">
            <a href="#" class="menu__tab">Se connecter</a>
        </li>
        <li class="menu__tab__el">
            <a href="#" class="menu__tab">Contact</a>
        </li>
    </ul>

    <ul class="menu__tab__li menu__tab__li--personal">
        <li class="menu__tab__el">
            <a href="#" class="menu__tab menu__tab--bold">Je suis</a>
        </li>
        <li class="menu__tab__el">
            <a href="#" class="menu__tab menu__tab--bold">Je trouve</a>
        </li>
    </ul>

    <ul class="dropdownMenu__li">
        <li class="dropdownMenu__el">
            <DropdownMenu title={'Ma ville'} tabs={dropdownTabPlaceholder}/>
        </li>
        <li class="dropdownMenu__el">
            <DropdownMenu title={'Vivre à Binche'} tabs={dropdownTabPlaceholder}/>
        </li>
        <li class="dropdownMenu__el">
            <DropdownMenu title={'Que faire à Binche'} tabs={dropdownTabPlaceholder}/>
        </li>
    </ul>
</div>