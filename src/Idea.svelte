<script>
    import { slide, blur } from 'svelte/transition';
    export let idea = {}
    export let loading;
    const suspenseDuration = 700
    const typesMap = {
        education: '🤓',
        recreational: '💃',
        social: '🥳',
        diy: '🧑‍🔧',
        charity: '😇',
        cooking: '🧑‍🍳',
        relaxation: '💆',
        music: '🧑‍🎤',
        busywork: '🧑‍💼'
    }
    $: emoji = loading ? '⌛' : typesMap[idea.type] || '😀'
</script>
<div  transition:slide="{{ duration:100 }}" class="m-2 px-4 py-6 border-2 border-amber-600 bg-gray-50 flex">
    <div class="w-1/6 flex items-center justify-center text-3xl" class:animate-spin="{loading}">{emoji}</div>
    <div class="flex-grow text-left">
        {#if loading}
            <h2 class="text-lg font-semibold text-amber-800 inline-block">Loading, wait a sec</h2>
        {:else}
            <h2 in:blur="{{ duration: suspenseDuration }}" class="text-lg font-semibold text-amber-800 border-b-2 border-amber-600 pb-4 mb-4">{idea.activity}</h2>
            <p in:blur="{{ duration: suspenseDuration }}" ><span class="font-light text-gray-600">People needed:</span> {idea.participants}</p>
        {/if}
    </div>
</div>