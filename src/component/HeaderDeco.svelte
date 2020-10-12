<script>
    // your script goes here
    import { onMount } from 'svelte';
    const distanceMin = 100;
    const displacementStrength = [28, 14, 8];

    let mouse = {x: 0, y: 0};
    let distanceFromMouse = {x: 0, y: 0};

    let block;
    let center = {x: 0, y: 0};

    let bubble1;
    let bubble2;
    let bubble3;

    onMount(async () => {
        document.addEventListener('mousemove', imgDisplacement);
        window.onresize = getBlockCenter;
        getBlockCenter();
	});

    function imgDisplacement(event){
        mouse.x = event.clientX;
        mouse.y = event.clientY;

        distanceFromMouse.x = event.clientX - center.x;
        distanceFromMouse.y = event.clientY - center.y;

        let normalizedDistance = getNormalizedDistance();

        bubble1.style.transform = `translate(${displacementStrength[0] * normalizedDistance.x}px,${displacementStrength[0] * normalizedDistance.y}px)`;
        bubble2.style.transform = `translate(${displacementStrength[1] * normalizedDistance.x}px,${displacementStrength[1] * normalizedDistance.y}px)`;
        bubble3.style.transform = `translate(${displacementStrength[2] * normalizedDistance.x}px,${displacementStrength[2] * normalizedDistance.y}px)`;
    }

    function getBlockCenter(){
        let b = block.getBoundingClientRect();
        center.x = b.x + (b.width / 2);
        center.y = b.top + (b.width / 2);

    }

    function getNormalizedDistance(){
        let normalizedDistance = {x: 0, y: 0};
        let hyp = Math.sqrt(distanceFromMouse.x * distanceFromMouse.x + distanceFromMouse.y * distanceFromMouse.y);

        normalizedDistance.x = distanceFromMouse.x / center.x;
        normalizedDistance.y = distanceFromMouse.y / center.y;

        return normalizedDistance;
    }
</script>

<style lang="scss">
    /* your styles go here */
    @import './style/_headerDeco.scss';
</style>

<!-- markup (zero or more items) goes here -->
<div class="header__deco needMouse" bind:this={block}>
    <img src="asset/img/party01.png" class="bubbleImg bubbleImg--main" alt="party01" bind:this={bubble1}/>
    <img src="asset/img/party02.png" class="bubbleImg bubbleImg--secondary" alt="party02" bind:this={bubble2}/>
    <span class="bubble" bind:this={bubble3}>Bubble</span>
</div>