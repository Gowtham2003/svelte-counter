<script>
	import {createEventDispatcher} from "svelte";
	const dispatcher = createEventDispatcher();
	
	export let counter;
</script>

<div class="row m-2">
	<div class="col-1 m-3">
		<span class="badge" class:bg-warning={counter.value===0} class:bg-primary={counter.value!==0}>{counter.value ===0 ? "Zero" : counter.value}</span>
	
	</div>
	<div class="col-4 m-2">
		<button class="btn btn-secondary" on:click={dispatcher("increment",{counter})}>
		+
	</button>
	<button class="btn btn-info" on:click={dispatcher("decrement",{counter})} disabled={counter.value===0}>
		-
	</button>
	<button class="btn btn-danger" on:click={dispatcher("delete",{counter})}>
		X
	</button>
</div>

	</div>
	