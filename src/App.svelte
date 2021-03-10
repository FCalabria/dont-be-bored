<script>
    import f from 'just-fetch'
    import Styles from './Styles.svelte'
    import Idea from './Idea.svelte'
    import Button from './microcomponents/Button.svelte'

    let getIdeaDisabled
    let idea

    async function getIdea () {
        getIdeaDisabled = true
        idea = await f.get('http://www.boredapi.com/api/activity/')
        getIdeaDisabled = false
    }
</script>
<Styles />

<main class="text-center mx-6 my-8">
	<h1 class="text-3xl mb-9">Are you bored? Don't be bored!</h1>
    <Button on:click={getIdea} text={"Get an idea"} disabled={getIdeaDisabled}/>
    <!-- Loading component for the idea (#await) -->
    {#if idea}<Idea {idea}/>{/if}
</main>
