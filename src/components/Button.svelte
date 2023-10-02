<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
</script>

<button
  class="bg-slate-700 text-white p-3 m-3 shadow-sm rounded-md hover:bg-teal-400 hover:text-stone-900"
  on:click={() => dispatch("changeOffset")}
>
  <slot />
</button>
