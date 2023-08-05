<script>
  //import { createEventDispatcher } from 'svelte';
  import { searchPokemon } from '$lib/SearchPokemonService.svelte';
  import {pokemonDataStor} from '$lib/Stories.svelte';

  let searchTerm = "";
  let searchTimeout;
  let pokemonData = null;

  //const dispatch = createEventDispatcher();

  async function handleSearchInput() {
    clearTimeout(searchTimeout);
    searchTimeout = setTimeout(async () => {
      pokemonData = await searchPokemon(searchTerm);
      //dispatch('pokemonDataChanged', pokemonData);
      pokemonDataStor.update(pokemonData);

    }, 400);
  }
</script>
<div class="input-container">
  <div class="input-with-icon">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Vector_search_icon.svg/709px-Vector_search_icon.svg.png"
      alt=""
    />
    <input
      class="search-pokemon"
      type="text"
      placeholder="Search Pokemon" bind:value={searchTerm} on:input={handleSearchInput}
    />
  </div>
</div>

<style>
.search-pokemon {
  width: 100%;
  border: 0;
  font-size: 20px;
}
.search-pokemon:focus {
  outline: 0;
}
.input-container {
  display: grid;
  grid-template-columns: 64px;
  transition: 500ms all ease;
  justify-content: center;
}
.input-container:hover,
.input-container:has(input:focus) {
  grid-template-columns: 100%;
}
::placeholder {
  color: transparent;
  opacity: 0; /* Firefox */
}
.search-pokemon:hover::placeholder,
.search-pokemon:focus::placeholder {
  color: grey;
  opacity: 1;
}
.input-with-icon {
  display: flex;
  border-radius: 30px;
  background-color: white;
  border: 1px solid gray;
  padding: 15px;
  align-items: center;
}
.input-with-icon img {
  max-width: 30px;
  margin-right: 10px;
}

</style>