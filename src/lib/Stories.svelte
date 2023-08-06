<script context="module">
import { writable } from 'svelte/store';

export const pokemonDataStor = writable(['empty']);
export const favoritePokemon = writable([]);

</script>