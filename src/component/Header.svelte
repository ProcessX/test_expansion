<script>
    // your script goes here
    import BtnIcon from "./BtnIcon.svelte";
</script>

<style lang="scss">
    /* your styles go here */
    @import './style/_header.scss';
</style>

<!-- markup (zero or more items) goes here -->
<header class="intro">
    <h1 class="title title--intro title--welcome">Header</h1>
    <p class="">Une ville proche du citoyen, qui informe au mieux la population de la vie communale</p>
    <BtnIcon title={'Que cherchez-vous ?'}/>
</header>