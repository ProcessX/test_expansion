<script>
    // your script goes here
    import BtnIcon from "./BtnIcon.svelte";
    import HeaderDeco from "./HeaderDeco.svelte";

    
</script>

<style lang="scss">
    /* your styles go here */
    @import './style/_header.scss';

    :global(.btnIcon){
        grid-column: 2/13;
        justify-self: start;

        @include for-size(desktop){
            grid-column: 3/13;
        }
    }
</style>

<!-- markup (zero or more items) goes here -->
<header class="intro">
    <h1 class="title title--intro title--welcome">Bienvenu à Binche<span class="title__deco">...</span></h1>
    <p class="intro__message">Une ville proche du citoyen, qui informe au mieux la population de la vie communale</p>
    <BtnIcon title={'Que cherchez-vous ?'} type={"search"}/>
    <HeaderDeco/>
</header>