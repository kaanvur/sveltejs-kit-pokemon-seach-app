<script context="module">
  export async function searchPokemon(searchTerm) {
      const response = await fetch(`https://pokedex.bgure.workers.dev/?q=${searchTerm}`);
      return await response.json();
  }
</script>