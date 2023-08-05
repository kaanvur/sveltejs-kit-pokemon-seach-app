<script>
	import List from './List.svelte';
	import Seachbox from './Searhbox.svelte';
</script>

<svelte:head>
	<title>Pokemon Search</title>
	<meta name="description" content="Pokemon Search app" />
</svelte:head>
<section>
	<Seachbox />
  <List />
</section>
<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}
</style>
