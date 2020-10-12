<script>
    // your script goes here
    import Dropdown from './Dropdown.svelte';

    export let dropdowns;

    let dropdownsOpen = new Array(dropdowns.length);
    dropdownsOpen.fill(false);

    function toggleDropdown(index){
        for(let i = 0; i < dropdownsOpen.length; i++){
            if(i == index)
                dropdownsOpen[i] = !dropdownsOpen[index];
            else
            dropdownsOpen[i] = false;
        }
    }

</script>

<style lang="scss">
    @import './style/_navbar.scss';
    @import './style/_dropdownList.scss';

    
</style>

<!-- markup (zero or more items) goes here -->
<ul class="dropdown__li">
    {#each dropdowns as dropdown, i}
        <li class="dropdown__el">
            <Dropdown
                title={dropdown.title}
                links={dropdown.links}
                toggleDropdown={toggleDropdown}
                index={i}
                open={dropdownsOpen[i]}
            />
        </li>
    {/each}
</ul>