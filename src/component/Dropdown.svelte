<script>
    // your script goes here
    export let title;
    export let links;

    let open = false;

    function toggleOpen(){
        open = !open;
    }
</script>

<style lang="scss">
    @import './style/_dropdown.scss';
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->
<div class="dropdown">
    <button on:click={toggleOpen} class="btn dropdown__btn {open ? "dropdown__btn--open" : ""}">{title}</button>
    <ul class="dropdown__link__li {open ? "dropdown__link__li--open" : ""}">
        {#each links as link}
            <li class="dropdown__link__el">
                <a href="{link.href}" class="dropdown__link">{link.title}</a>
            </li>
        {/each}
    </ul>
</div>