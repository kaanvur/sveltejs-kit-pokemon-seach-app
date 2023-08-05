<script context="module">
  export async function searchPokemon(searchTerm) {
    if (searchTerm) {
      const response = await fetch(`https://pokedex.bgure.workers.dev/?q=${searchTerm}`);
      return await response.json();
    } else {
      return null;
    }
  }
</script>