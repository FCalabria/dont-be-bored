<script>
    export let idea = {}
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
    $: emoji = typesMap[idea.type] || '😀'
</script>
<div class="m-2 px-2 py-6 border-2 border-amber-600 bg-gray-50 flex">
    <div class="w-1/6 flex items-center justify-center text-3xl">{emoji}</div>
    <div class="flex-grow text-left">
        <h2 class="text-lg font-semibold text-amber-800 border-b-2 border-amber-600 pb-4 mb-4">{idea.activity}</h2>
        <p><span class="font-light text-gray-600">People needed:</span> {idea.participants}</p>
    </div>
</div>