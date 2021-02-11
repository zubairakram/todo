<script>
    import { onMount } from "svelte";
import { items } from '../stores.js';
import TodoApi from "../TodoApi.js";
import Item from "./Item.svelte"

function handleNewItem(e) { 
}

function handleUpdate(e) { 
    console.log("updating item!");
}

function handleDelete(e) { 
}

onMount(async () => {
    $items = await TodoApi.getAll();
    $items = [];
})
</script>

<style>
    .list {
        padding: 15px;
    }
    .list-status {
        margin: 0;
        text-align: center;
        color: rgb(255, 255, 255);
        font-weight: bold;
        font-size: 1.1em;
    }
</style>

<div class="list">
    {#each $items as item (item)}
        <Item {...item} on:update={handleUpdate} on:delete={handleDelete}></Item>
    {:else}
        <p class="list-status">No Items Exist</p>
    {/each}
</div>
