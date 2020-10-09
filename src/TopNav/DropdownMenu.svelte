<script>
    // your script goes here
    export let title;
</script>

<style type="text/scss">
    /* your styles go here */

    .dropdownMenu{
        
    }

    .btn--dropdown{
        cursor: pointer;
        font-weight: bold;
        background-color: transparent;
        border: none;
        padding: 0;
        margin: 0;

        &:after{
            display: inline-block;
            content: 'drop';
            height: 1rem;
            width: 1rem;
            max-width: 1rem;
            max-height: 1rem;
            margin-left: 0.5rem;
            overflow: hidden;
            text-indent: 100%;
            background-color: gray;
            transform-origin: center;
        }

        &:hover{
            &:after{
                transform: scale(120%);
            }
        }
    }
</style>

<!-- markup (zero or more items) goes here -->

<div class="dropdownMenu">
    <button class="btn btn--dropdown">{title}</button>
    <ul class="tab__li">
        <li class="tab__el">
            
        </li>
    </ul>
</div>