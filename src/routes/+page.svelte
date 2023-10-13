<script lang="ts">
	import { createStack } from "$lib/stack";
	import Item from "./Item.svelte";

    const stack = createStack<string[]>([])

    function add() {
        stack.push((v) => {
            v.push('value')
            return v
        })
    }
</script>

<div class="">

    <button on:click={add}>add</button>
</div>

{#each $stack.current as item }
    <Item bind:item/>
{/each}