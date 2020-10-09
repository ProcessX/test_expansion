<script>
    // your script goes here
    import BtnWithIcon from '../Btn/BtnWithIcon.svelte';
</script>

<style type="text/scss">
    /* your styles go here */

    $green-cream: #C1DFC4;
    $orange: #EA5B0C;

    $titleCircleSize: 250px;

    header{
        padding: 15rem 1rem 15rem 1rem;
        background-color: $green-cream;
    }

    .title--header{
        font-size: 64px;
        position: relative;
        margin-top: 0;
        z-index: 10;

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
    }

    .text--intro{
        font-weight: bold;
        font-size: 28px;
    }
</style>

<!-- markup (zero or more items) goes here -->

<header>
    <h1 class="title title--header">Bienvenue à Binche...</h1>
    <p class="text text--intro">Une ville proche du citoyen, qui informe au mieux la population de la vie communale</p>
    <BtnWithIcon title={'Que cherchez-vous ?'}/>
</header>