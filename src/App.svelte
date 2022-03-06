<script lang='ts'>
import {marked} from 'marked'
import MdEditor from './components/mdEditor.svelte'

</script>

<main class="w-screen h-screen min-h-screen bg-slate-200 flex flex-col items-center">
  <h1 class="text-3xl font-semibold m-4">Post Editor</h1>
  <MdEditor />
  
</main>