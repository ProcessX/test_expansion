<script>
    // your script goes here

    export let title;
    export let links;
    export let toggleDropdown;
    export let index;
    export let open = false;

    let magnetize = false;

    const magnetizeStrength = 10;

    let mouse = {x: 0, y: 0};
    let distanceFromMouse = {x: 0, y: 0};

    let block;
    let btn;
    let center = {x: 0, y: 0};
    let blockDimension;

    $: {
        if(open){
            magnetize = false;
        }
        else{
            magnetize = true;
        }

        resetBtn();
    }

    function resetBtn(){
        if(btn)
            btn.style.transform = `translate(${0}px,${0}px) scale(${open ? "110%" : "100%"})`;
    }

    
    function mouseEnter(){
        if(!open){
            magnetize = true;
            blockDimension = block.getBoundingClientRect();
            getBlockCenter(); 
        }
    }

    function mouseLeave(){
        if(!open){
            magnetize = false;
            btn.style.transform = `translate(${0}px,${0}px)`;
        }
    }

    function moveBlock(event){
        
        if(magnetize){
            mouse.x = event.clientX;
            mouse.y = event.clientY;

            distanceFromMouse.x = event.clientX - center.x;
            distanceFromMouse.y = event.clientY - center.y;

            let normalizedDistance = getNormalizedDistance();
            btn.style.transform = `translate(${magnetizeStrength * normalizedDistance.x}px,${magnetizeStrength * normalizedDistance.y}px)`;
        }
    }

    function getBlockCenter(){
        center.x = blockDimension.left + (blockDimension.width / 2);
        center.y = blockDimension.top + (blockDimension.height / 2);
    }

    function getNormalizedDistance(){
        let normalizedDistance = {x: 0, y: 0};

        normalizedDistance.x = (distanceFromMouse.x / blockDimension.width) * 2;
        normalizedDistance.y = (distanceFromMouse.y / blockDimension.height) * 2;

        return normalizedDistance;
    }
</script>

<style lang="scss">
    @import './style/_dropdown.scss';
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->
<div class="dropdown {open ? "dropdown--open" : ""}" bind:this={block} on:mousemove={moveBlock} on:mouseenter={mouseEnter} on:mouseleave={mouseLeave}>
    <button bind:this={btn} on:click={toggleDropdown(index)} class="btn dropdown__btn {open ? "dropdown__btn--open" : ""}">{title}</button>
    <ul class="dropdown__link__li {open ? "dropdown__link__li--open" : ""}">
        {#each links as link}
            <li class="dropdown__link__el">
                <a href="{link.href}" class="dropdown__link">{link.title}</a>
            </li>
        {/each}
    </ul>
</div>