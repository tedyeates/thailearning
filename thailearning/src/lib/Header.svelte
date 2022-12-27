<script lang="ts">
	import { page } from '$app/stores'

    type Header = {
        id: string
        name: string
    }
	export let headers: Array<Header>
</script>

<header>
	<nav>
		<ul>
			{#each headers as {id, name}}
			<li class:active={$page.url.pathname === `/${id}`}>
				<a href={`/${id}`}>{name}</a>
			</li>
			{/each}
		</ul>
	</nav>
</header>

<style lang="sass">
	@use 'shared.sass'

	nav
		background-color: shared.$secondary-color
		width: 100%
		height: shared.$navbar-height
		top: 0
		left: 0

		position: fixed
		display: flex
		justify-content: space-between

		a
			color: shared.$primary-color
			text-decoration: none
			padding: 1rem
			font-size: 1rem

			// Default position
			position: relative
			font-weight: 300
			transition: font-weight .4s ease

		// On fade
		a:hover
			font-weight: 900

	li
		display: inline-block

</style>
