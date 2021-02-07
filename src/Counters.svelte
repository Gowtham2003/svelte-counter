<script>
	import Counter from "./Counter.svelte";
	import {createEventDispatcher} from "svelte";
	const dispatcher = createEventDispatcher();
	
	
	export let counters;

</script>

<div class="m-2">
	<button class="btn btn-info" on:click={dispatcher("new",{counters})}>
	New
</button>
<button class="btn btn-warning" on:click={dispatcher("reset",{counters})}>
	Reset
</button>
{#each counters as counter}
	<Counter on:increment={dispatcher("increment",{counter})} on:decrement={dispatcher("decrement",{counter})} on:delete={dispatcher("delete",{counter})} {counter}/>
{/each}

</div>
