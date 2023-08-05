<script>
  import {pokemonDataStor} from '$lib/Stories.svelte';
	let pokemonData = 'boş';
  
	pokemonDataStor.subscribe((value) => {
		pokemonData = value;
	});
</script>
{#if pokemonData == 'boş'}
  <h2>Pokemon Ara</h2>
{:else if pokemonData.length > 0}
{pokemonData}
  <h2>Pokemon Listesi</h2>
  <section class="list-holder">
    {#each pokemonData as pokemon}
      <div>
        <img src={pokemon.photo} alt={pokemon.name} />
        <p>{pokemon.name}</p>
      </div>
    {/each}
  </section>
{:else}
  <h2>Böyle bir Pokemon bulunamadı.</h2>
{/if}

<style>
  .list-holder {
    display: grid;
    gap: 10px;
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }

  .list-holder > * {
    box-shadow: 6px 6px 5px #000000;
    border-radius: 5px;
    aspect-ratio: 4 / 6;
    background-color: #e5e5f7;
    background-image: repeating-radial-gradient(
        circle at 0 0,
        transparent 0,
        #e5e5f7 10px
      ),
      repeating-linear-gradient(#edfd6355, #edfd63);
    display: grid;
    align-items: center;
    text-align: center;
  }

  .list-holder img {
    margin-bottom: auto;
    width: 100%;
  }

  h1,
  h2 {
    text-align: center;
    margin: 2vmin 0;
  }
</style>
