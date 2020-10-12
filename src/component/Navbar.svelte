<script>
    // your script goes here
    import Burger from './Burger.svelte';
    import DropdownList from './DropdownList.svelte';

    let menuOpen = false;
    let page;

    let dropdownLinks_placeholder = [
        {title: "link01",href: "#"},
        {title: "link02",href: "#"},
        {title: "link03",href: "#"},
    ];

    let dropdowns = [
        {
            title: "Ma ville",
            links: dropdownLinks_placeholder,
        },
        {
            title: "Vivre à Binche",
            links: dropdownLinks_placeholder,
        },
        {
            title: "Que faire à Binche",
            links: dropdownLinks_placeholder,
        },
    ]

    function toggleMenu(){
        menuOpen = !menuOpen;
        if(!page){
            page = document.getElementsByClassName('page')[0];
        }
        document.body.classList.toggle('lockScroll');
    }

</script>

<style lang="scss">
    @import './style/_navbar.scss';
    /* your styles go here */

</style>

<!-- markup (zero or more items) goes here -->
<nav class="navbar {menuOpen ? "navbar--menuOpen" : ""}">
    <a href="#" class="navbar__link navbar__link--logo">Logo</a>

    <Burger onclick={toggleMenu}/>

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

        <DropdownList dropdowns={dropdowns}/>

    </div>
</nav>