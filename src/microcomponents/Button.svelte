<script>
    export let text = 'Click me';
    export let disabled = false;
</script>
<button
    class="py-3 px-5 border-2 border-blue-600 text-blue-600 bg-white hover:text-white hover:border-white hover:bg-blue-600 focus:text-white focus:border-white focus:bg-blue-600 disabled:bg-blue-300 disabled:cursor-not-allowed"
    on:click
    {disabled}
>{text}</button>