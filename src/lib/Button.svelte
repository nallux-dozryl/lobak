<script>
    let { animal, selected, theme } = $props();
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
</script>
<button
    class:doInvert={theme === 'black'}
    class="border-2 border-black size-16 cursor-pointer {selected ? '': 'hover:scale-110'} transition-all duration-300 {selected ? 'scale-120' : ''}"
    onclick={() => {
        dispatch('click', animal);
    }}
    >
    <img src="/{animal}.svg" alt="{animal} Roll"/>
</button>    

<style>
    .doInvert {
        filter: invert(1);
    }
</style>