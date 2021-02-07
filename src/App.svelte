<script>
  import Navbar from "./Navbar.svelte";
	import Counters from "./Counters.svelte";
	
	let counters = [{id:1,value:0},{id:2,value:0},{id:3,value:0}];
	
	
		const handleIncrement = (e) => {
		const idx = counters.findIndex(x=> x.id===e.detail.counter.id);
		const element = counters[idx];
		element.value += 1;
		counters[idx] = element;
		counters = counters;
	}
	
	const handleDecrement = (e) => {
		const idx = counters.findIndex(x=> x.id===e.detail.counter.id);
		const element = counters[idx];
		element.value -= 1;
		counters[idx] = element;
		counters = counters;
	}
	
	const handleDelete = (e) => {
		counters = counters.filter(x=>x.id!==e.detail.counter.id)
	}
	
	const handleReset = (e) => {
		counters = counters.map(counter => counter={...counter,value:0})
	}
	
	const handleNew = (e) => {
		counters = [...counters,{id:counters.length+1,value:0}]
	}
	
</script>
<svelte:head>
	<!-- CSS only -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-giJF6kkoqNQ00vy+HMDP7azOuL0xtbfIcaT9wjKHr8RbDVddVHyTfAAsrekwKmP1" crossorigin="anonymous">

</svelte:head>
<Navbar items={counters.length}/>
<main class="container"><Counters on:increment={handleIncrement} on:decrement={handleDecrement} on:delete={handleDelete} on:reset={handleReset} on:new={handleNew} {counters}/></main>
