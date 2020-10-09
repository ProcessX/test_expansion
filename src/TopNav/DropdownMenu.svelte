<script>
    // your script goes here
    export let title;
    export let tabs;

    let open = false;

    function toggleOpen(){
        open = !open;
    }
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

    .tab__li{
        background-color: red;
        list-style: none;
        padding: 0;
        max-height: 0px;
        overflow: hidden;

        &--open{
            max-height: none;
        }
    }

    .tab__el{
        padding: 1rem;
    }
</style>

<!-- markup (zero or more items) goes here -->

<div class="dropdownMenu">
    <button class="btn btn--dropdown" on:click={toggleOpen}>{title}</button>
    <ul class="tab__li {open ? 'tab__li--open' : ''}">
        {#each tabs as tab}
            <li class="tab__el">
                <a class="tab" href="{tab.link}">{tab.title}</a>
            </li>
        {/each}
    </ul>
</div>