<script lang="ts">
	import Header from '$lib/Header.svelte'
	import '../app.sass'

	let headers = [
		{
			id: "body",
			name: "Body Parts"
		}
	]
</script>

<Header headers={headers} />

<main>
	<slot />
</main>

<style lang="sass">
	@use '../lib/shared.sass'

	main
		margin-top: shared.$navbar-height
</style>