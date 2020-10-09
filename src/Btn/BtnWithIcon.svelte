<script>
    // your script goes here
    export let title;
    export let type;
</script>

<style type="text/scss">
    /* your styles go here */

    $iconSize: 50px;
    $lineHeight : 1.4;

    $orange-light: #FED386;

    .btn{
        cursor: pointer;
        display: inline-block;
    }

    .btn--withIcon{
        font-weight: bold;
        color: black;
        text-decoration: none;
        position: relative;
        padding-left: $iconSize + 10px;
        box-sizing: border-box;
        line-height: $lineHeight;

        &:before{
            display: inherit;
            content: 'Icon';
            height: $iconSize;
            width: $iconSize;
            max-height: $iconSize;
            max-width: $iconSize;
            border-radius: 100%;
            text-indent: 100%;
            overflow: hidden;
            position: absolute;
            left: 0;
            top: -($iconSize - $lineHeight) / 2;
            transform-origin: center;
            background-size: 42%;
            background-repeat: no-repeat;
            background-position: center ;


            background-color: gray;
        }

        &:hover{
            &:before{
                transform: scale(120%);
            }
        }
    }

    .btn--withIcon--search{
        &:before{
            background-image: url('/asset/icon/search.svg');
            background-color: $orange-light;
        }
    }
</style>

<!-- markup (zero or more items) goes here -->

<a href="#" class="btn btn--withIcon" class:btn--withIcon--search={type='search'}>{title}</a>