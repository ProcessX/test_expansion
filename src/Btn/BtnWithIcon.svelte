<script>
    // your script goes here
    export let title;
</script>

<style type="text/scss">
    /* your styles go here */

    $iconSize: 2em;
    $lineHeight : 1.4em;

    .btn{
        cursor: pointer;
        display: inline-block;
    }

    .btn--withIcon{
        font-weight: bold;
        color: black;
        text-decoration: none;
        position: relative;
        padding-left: $iconSize + 1em;
        box-sizing: border-box;
        line-height: $lineHeight;

        &:before{
            display: inherit;
            content: 'Icon';
            height: $iconSize;
            width: $iconSize;
            max-height: $iconSize;
            max-width: $iconSize;
            text-indent: 100%;
            overflow: hidden;
            position: absolute;
            left: 0;
            top: -($iconSize - $lineHeight) / 2;
            transform-origin: center;

            background-color: gray;
        }

        &:hover{
            &:before{
                transform: scale(120%);
            }
        }
    }
</style>

<!-- markup (zero or more items) goes here -->

<a href="#" class="btn btn--withIcon">{title}</a>