<script lang="ts">
    import Icon from '@iconify/svelte'
    import {v4 as uuid} from 'uuid'
    import fs from 'fs'
    export let content:string;
    export let title:string;

    let html = false
    const toggleHTML = () => {
        alert('Feature Not available yet😔')
    }
    const toggleSave = () => {
        console.log('saved')
        let data = {
            id: uuid(),
            title: title,
            author: 'Matiss',
            lastEdited: Date.now(),
            body: content
        }
        let parsedData = JSON.stringify(data)
        fs.writeFile(`../data/drafts/${data.id}`, parsedData, (err) => {console.log(err)})
    }
    const toggleDelete = () => {

    }
</script>

<div class="bg-red-500 w-full h-16 my-4 rounded-md flex flex-row justify-end items-center">
    {#if html}
    <button on:click={toggleHTML} class="bg-red-400 hover:bg-red-300  rounded-full w-12 h-12 mx-2 flex justify-center items-center"><Icon icon="bi:markdown" color="white" class='w-8 h-8' /></button>
    {:else}
    <button on:click={toggleHTML} class="bg-red-400 hover:bg-red-300  rounded-full w-12 h-12 mx-2 flex justify-center items-center"><Icon icon="dashicons:html" color="white" class='w-8 h-8' /></button>
    {/if}
    <button on:click={toggleDelete} class="bg-red-400 hover:bg-red-300  rounded-full w-12 h-12 mx-2 flex justify-center items-center"><Icon icon="ant-design:delete-outlined" color="white" class='w-8 h-8' /></button>
    <button on:click={toggleSave} class="bg-red-400 hover:bg-red-300  rounded-full w-12 h-12 mx-2 flex justify-center items-center"><Icon icon="ant-design:save-outlined" color="white" class='w-8 h-8'/></button>
</div>