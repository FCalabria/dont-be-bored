<script>
    import { createEventDispatcher } from 'svelte';
    import Button from './microcomponents/Button.svelte'
    import { types } from './types'
    let filtersOpen = false
    let type
    const dispatch = createEventDispatcher();

    function capitalize (type) {
        return type[0].toUpperCase() + type.slice(1)
    }
    function changeFilter () {
        dispatch('filterChange', { type })
    }

</script>
<div class="inline-block">
    <Button on:click="{() => filtersOpen = !filtersOpen}" text={`Filters ${ filtersOpen ? '>' : '<'}`}/>
    {#if filtersOpen}
        <div class="inline-block p-3 text-blue-600 border-2 border-blue-600 bg-white focus-within:bg-blue-600 focus-within:text-white hover:bg-blue-600 hover:text-white">
            <label class="" for="type">Type:</label>
            <select class="capitalize appearance-none bg-transparent" on:blur={changeFilter} bind:value={type} name="type" id="type">
                <option value="">Any</option>
                {#each types as type}
                    <option value={type}>{capitalize(type)}</option>
                {/each}
            </select>
        </div>
    {/if}
</div>