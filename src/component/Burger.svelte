<script>
    // your script goes here

    export let onclick = () => {}; 

    let open = false;

    function toggleOpen(){
        open = !open;
        onclick();
    }
</script>

<style lang="scss">
    /* your styles go here */
    @import './style/_burger.scss';
</style>

<!-- markup (zero or more items) goes here -->

<button class="btn burger {open ? "burger--open" : ""}" on:click={toggleOpen}>Burger</button>