<script>
  export let name;
  import { fetchPokemonData } from "../utils/fetchPokemonData";
</script>

<div class="flex flex-col justify-center items-center">
  {#await fetchPokemonData(name)}
    <p>Loading {name}....</p>
  {:then data}
    <img src={data.sprites.front_default} alt={data.name} class="w-52" />
    <h1 class="text-3xl font-bold m-2 text-slate-400">{name}</h1>
    <div class="flex flex-col md:flex-row">
      <div class="m-2">
        <h1 class="text-xl bg-slate-700 text-white rounded-md p-2 flex justify-center">Stats</h1>
        <div class="flex flex-col mt-5 bg-slate-700 rounded-md p-4">
          {#each data.stats as stat}
            <h2 class="text-slate-400">{stat.stat.name}: {stat.base_stat}</h2>
          {/each}
        </div>
      </div>
      <div class="m-2">
        <h1 class="text-xl bg-slate-700 text-white rounded-md p-2 flex justify-center">Types</h1>
        <div class="flex flex-col mt-4 bg-slate-700 rounded-md p-4">
          {#each data.types as type}
            <h2 class="text-slate-400">{type.type.name}</h2>
          {/each}
        </div>
      </div>
    </div>
  {/await}
</div>
