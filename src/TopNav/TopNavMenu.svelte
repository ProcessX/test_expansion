<script>
    // your script goes here
    import DropdownMenu from './DropdownMenu.svelte';
</script>

<style type="text/scss">
    /* your styles go here */
    $green-cream: #C1DFC4;
    $orange: #EA5B0C;

    .topNav__menu{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        background-color: red;
        //display: none;
    }

    .menu__tab__li{
        list-style: none;
        padding: 0;
        margin: 0;
    }

    .menu__tab__el{

    }

    .menu__tab{
        color: black;
        text-decoration: none;
    }
</style>

<!-- markup (zero or more items) goes here -->
<div class="topNav__menu">
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
            <a href="#" class="menu__tab">Je suis</a>
        </li>
        <li class="menu__tab__el">
            <a href="#" class="menu__tab">Je trouve</a>
        </li>
    </ul>

    <ul class="dropdownMenu__li">
        <li class="dropdownMenu__el">
            <DropdownMenu/>
        </li>
    </ul>
</div>