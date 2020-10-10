<script>
    // your script goes here
    import Dropdown from './Dropdown.svelte';

    let menuOpen = false;

    let dropdownLinks_placeholder = [
        {title: "link01",href: "#"},
        {title: "link02",href: "#"},
        {title: "link03",href: "#"},
    ];

    function toggleMenu(){
        menuOpen = !menuOpen;
    }
</script>

<style lang="scss">
    @import './style/_navbar.scss';
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->
<nav class="navbar {menuOpen ? "navbar--menuOpen" : ""}">
    <a href="#" class="navbar__link navbar__link--logo">Logo</a>
    <button class="btn navbar__burger" on:click={toggleMenu}>Burger</button>

    <div class="navbar__menu {menuOpen ? "navbar__menu--open" : ""}">
        <ul class="navbar__link__li">
            <li class="navbar__link__el">
                <a href="#" class="navbar__link">Contact</a>
            </li>
            <li class="navbar__link__el">
                <a href="#" class="navbar__link">Se connecter</a>
            </li>
            <li class="navbar__link__el navbar__link__el--bold">
                <a href="#" class="navbar__link">Je trouve</a>
            </li>
            <li class="navbar__link__el navbar__link__el--bold">
                <a href="#" class="navbar__link">Je suis</a>
            </li>
        </ul>

        <ul class="dropdown__li">
            <li class="dropdown__el">
                <Dropdown title={"Ma ville"} links={dropdownLinks_placeholder}/>
            </li>
            <li class="dropdown__el">
                <Dropdown title={"Vivre à Binche"} links={dropdownLinks_placeholder}/>
            </li>
            <li class="dropdown__el">
                <Dropdown title={"Que faire à Binche"} links={dropdownLinks_placeholder}/>
            </li>
        </ul>
    </div>
</nav>