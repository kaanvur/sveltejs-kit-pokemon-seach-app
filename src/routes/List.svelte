<script>
  import {pokemonDataStor,favoritePokemon} from '$lib/Stories.svelte';
	let pokemonData;
  
	pokemonDataStor.subscribe((value) => {
		pokemonData = value;
	});
  let addPokemonToFavorite = (pokemon) => {
    favoritePokemon.update(pokemonList => {
      const duplicate = pokemonList.some(item => item.id === pokemon.id);
      if (!duplicate) {
        return [...pokemonList, pokemon];
      }
      return pokemonList;
    });
  }
</script>
{#if pokemonData[0] == 'empty'}
  <h2>Search Pokemon</h2>
{:else if pokemonData.length > 0}
  <h2>Pokémon List</h2>
  <section class="list-holder">
    {#each pokemonData as pokemon}
      <div on:click={addPokemonToFavorite(pokemon)}>
        <img src={pokemon.photo} alt={pokemon.name} />
        <p>{pokemon.name}</p>
      </div>
    {/each}
  </section>
{:else}
  <h2>this pokemon never existed</h2>
{/if}

<style>
  .list-holder {
    display: grid;
    gap: 10px;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    width: 100%;
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
