<script lang="ts">
import { marked } from 'marked'
import markedImages from 'marked-images'
import Buttons from './editorButtons.svelte'
marked.use(markedImages)
$: content = ''
$: parsedContent = ''
$: title = ''


</script>

<div class="h-4/5 w-4/5 flex flex-row justify-between">
    <div class="w-1/2 p-4 relative">
        <input class='w-full rounded-md p-3' type="text" placeholder="Title" bind:value={title}>
        <textarea bind:value={content} placeholder="Let's get writing 🚀" class="relative overflow-y-auto w-full h-full my-8 p-3 resize-none rounded-md drop-shadow-lg" id="MD-Editor"></textarea>

    </div>
    <div class="w-1/2 p-4">
        <div id="mdpreview" class="w-full h-full rounded-lg drop-shadow-lg p-3 bg-white prose max-w-none overflow-y-auto prose-img-sm">
            <h1 class="font-semibold">{title}</h1>
            {@html marked.parse(content)}
        </div>
        <Buttons title={title} content={content}/>
    </div>

</div>

