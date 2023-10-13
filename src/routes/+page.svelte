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

<p class="">
    Open console and click the add button, for some reason there is a second update happening after then first one and the value passed to that updfate is the value of the entire store not just $stack.current
</p>