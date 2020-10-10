<script>
    // your script goes here
    export let title;
    export let links;
</script>

<style lang="scss">
    @import './style/_dropdown.scss';
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->
<div class="dropdown">
    <button class="btn dropdown__btn">{title}</button>
    <ul class="dropdown__link__li">
        {#each links as link}
            <li class="dropdown__link__el">
                <a href="{link.href}" class="dropdown__link">{link.title}</a>
            </li>
        {/each}
    </ul>
</div>