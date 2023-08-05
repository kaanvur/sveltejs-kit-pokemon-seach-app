<script context="module">
  export async function searchPokemon(searchTerm) {
    /*if(searchTerm == '') {
      return ['boş']
    }
    else {*/
      const response = await fetch(`https://pokedex.bgure.workers.dev/?q=${searchTerm}`);
      return await response.json();
  }
  //}
</script>