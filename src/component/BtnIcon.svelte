<script>
    // your script goes here
    export let title;
    export let type;

    
</script>

<style lang="scss">
    /* your styles go here */
    @import './style/_btnIcon.scss';
</style>

<!-- markup (zero or more items) goes here -->
<button class="btn btnIcon {type ? `btnIcon--${type}` : ""}">{title}</button>