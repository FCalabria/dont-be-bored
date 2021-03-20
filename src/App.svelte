<script>
    import f from 'just-fetch'
    import Styles from './Styles.svelte'
    import Idea from './Idea.svelte'
    import Button from './microcomponents/Button.svelte'
    import Filters from './Filters.svelte'

    let idea
    let ideaLoading
    let filters = {}

    async function getIdea () {
        ideaLoading = true
        const baseUrl = 'http://www.boredapi.com/api/activity'
        const url = Object.entries(filters)
            .reduce((url, filter) => {
                const glue = url.includes('?') ? '&' : '?'
                url += `${glue}${filter[0]}=${filter[1]}`
                return url
            }, baseUrl)

        idea = await f.get(url, filters)
        ideaLoading = false
    }

</script>
<Styles />

<main class="text-center mx-6 my-8">
	<h1 class="text-3xl mb-9">Are you bored? Don't be bored!</h1>
    <Button class="m-2" on:click={getIdea} text={"Get an idea"} disabled={ideaLoading}/>
    <Filters on:filterChange={event => filters = event.detail}/>
    {#if idea || ideaLoading}<Idea {idea} loading={ideaLoading}/>{/if}
</main>
