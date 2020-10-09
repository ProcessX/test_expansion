<script>
    // your script goes here
    import BtnWithIcon from '../Btn/BtnWithIcon.svelte';
    import HeaderDeco from './HeaderDeco.svelte';
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
        }
    }

    $green-cream: #C1DFC4;
    $orange: #EA5B0C;

    $titleCircleSize: 250px;

    header{
        padding: 15rem 1rem 20rem 1rem;
        background-color: $green-cream;
        position: relative;
        box-sizing: content-box;

        &:before{
            content: "";
            display: inline-block;
            height: $titleCircleSize;
            width: $titleCircleSize;
            background-color: $orange;
            border-radius: 100%;
            position: absolute;
            left: -100px;
            top: 130px;
            //left: -($titleCircleSize / 2);
            //top: -($titleCircleSize / 2);;
            //z-index: -5;
        }

        @include for-size(tablet){
            //padding-left: calc((100% / 12) * 2);
            padding-left: calc((100% / 12) + 1rem);
            padding-bottom: 10rem;

            &:before{
                left: 1rem;
                top: 130px;
            }
        }

        @include for-size(desktop){
            //padding-left: 50px;
            padding-right: 50px;
            padding-left: calc((100% / 8) + 50px);
            /*
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            grid-template-rows: auto auto 1fr;
            */

            &:before{
                left: 50px;
            }
        }
    }

    .title--header{
        font-size: 64px;
        position: relative;
        margin-top: 0;
        margin-bottom: 115px;
        z-index: 10;
        display: inline-block;

        &--orange{
            color: $orange;
        }

/*
        &:before{
            content: "";
            display: inline-block;
            height: $titleCircleSize;
            width: $titleCircleSize;
            background-color: $orange;
            border-radius: 100%;
            position: absolute;
            left: -($titleCircleSize / 2);
            top: -($titleCircleSize / 2);;
            z-index: -5;
        }
        */

        @include for-size(tablet){
            color: rgba($color: #000000, $alpha: 0.0);
            /*
            grid-column: 2/12;
            grid-row: 1/2;
            */

            text-indent: 100%;
            white-space: nowrap;
            overflow: hidden;

            &--orange{
                color: inherit;
            }

            &:after{
                content: '';
                height: 100%;
                width: 100%;
                position: absolute;
                top: 0;
                left: 0;
                background-image: url('/asset/img/headline.svg');
                background-size: contain;
                background-repeat: no-repeat;
                background-position: center;
            }
        }

        @include for-size(desktop){
            font-size: 72px;
            justify-self: left;
        }
    }

    .text--intro{
        font-weight: bold;
        font-size: 28px;
        margin-top: 0;
        margin-bottom: 119px;
        max-width: 420px;

        @include for-size(tablet){
            
        }

        @include for-size(desktop){
            /*
            grid-row: 2/3;
            grid-column: 2/6;
            align-self: start;
            */
        }
    }

    @include for-size(desktop){

    }

/*
    :global(header .btn--withIcon){
        @include for-size(desktop){
            grid-row: 3/4;
            grid-column: 2/6;
            align-self: start;
        }
    }

    :global(header .header__deco){

        @include for-size(desktop){
            position: relative !important;
            width: 100% !important;
            top: 0;
            height: 100px;
            //align-self : center;
            grid-row: 2/3;
            grid-column: 7/13;
            padding: 0 !important;

            .imgBubble{
                position: absolute;
            }

            .imgBubble--secondary{
                top: 100% !important;
            }
        }
    }
    */
</style>

<!-- markup (zero or more items) goes here -->

<header>
    <h1 class="title title--header">Bienvenue à Binche<span class='title--header--orange'>...</span></h1>
    <p class="text text--intro">Une ville proche du citoyen, qui informe au mieux la population de la vie communale</p>
    
    <BtnWithIcon
        title={'Que cherchez-vous ?'}
        type={'search'}
    />
    
    <HeaderDeco/>
</header>