<script>
    import '@fontsource-variable/cinzel';
    import Button from '$lib/Button.svelte';
    import Pork from '$lib/Ingredients/Pork.svelte';
    import Crab from '$lib/Ingredients/Crab.svelte';
    import PorkSteps from '$lib/PorkSteps.svelte';
    import CrabSteps from '$lib/CrabSteps.svelte';

    let selected = $state('pork');
    let theme = $state('white');
</script>

<div class="flex flex-col items-center justify-center w-screen px-8 overflow-x-hidden {theme === 'white' ? 'bg-white text-black' : 'bg-black text-white'} relative">
    <button
        class="absolute top-0 right-0 border-2"
        onclick={() => theme = theme === 'white' ? 'black' : 'white'}>
        {#if theme === 'white'}
            <img src="/mj-black.png" class="w-8" alt="mj-black"/>
        {:else}
            <img src="/mj-white.avif" class="w-8" alt="mj-white"/>
        {/if}
    </button>
    <h1 class="text-xl font-bold underline m-4 mb-8">Chuah Family Penang Lobak</h1>
    <div class="flex gap-8">
        <Button animal="pork" {theme} selected={selected === 'pork'} on:click={() => selected = 'pork'}/>
        <Button animal="crab" {theme} selected={selected === 'crab'} on:click={() => selected = 'crab'}/>
    </div>
    <div class="w-[600px] max-w-full"> 
        <h3 class="text-md m-4 underline mt-8">Ingredients</h3>
        {#if selected === 'pork'}
            <Pork />
        {:else if selected === 'crab'}
            <Crab />
        {/if}
    </div>
    <div class="w-[600px] max-w-full"> 
        <h3 class="text-md m-4 underline mt-8">Preparation</h3>
        {#if selected === 'pork'}
            <PorkSteps />
        {:else if selected === 'crab'}
            <CrabSteps />
        {/if}
    </div>
</div>

<style>
    :global(body) {
        font-family: 'Cinzel Variable', serif;
    }
</style>
