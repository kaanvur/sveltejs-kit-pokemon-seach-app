<script>
  import {favoritePokemon} from '$lib/Stories.svelte';
  

</script>
<div class="favorite-list">
  {#each $favoritePokemon as pokemon}
  
    <div class="favorite-pokemon">
      <img src="https://cdn-icons-png.flaticon.com/512/164/164608.png" alt="" />
      { pokemon.name }
    </div>
  {/each}
</div>

<style>
.favorite-list {
  display: flex;
  overflow: auto;
  gap: 5px;
  height: 9vmin;
}
.favorite-list > * {
  flex-shrink: 0;
  font-size: 2vmin;
  text-align: center;
}
.favorite-list img {
  height: 50%;
  display: block;
  margin: 0 auto;
}

</style>