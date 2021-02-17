<script>
    import Styles from './Styles.svelte'
	export let name;
</script>
<Styles />

<main class="text-center m-6">
	<h1 class="text-3xl">Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>
