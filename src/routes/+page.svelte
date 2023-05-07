<script>
  import Rolodex from '$lib/rolodex/Rolodex.svelte'
	import { onMount } from 'svelte'
	import { readable } from 'svelte/store'

	export let start

	onMount(() => {
		start = new Date().getTime()
	})
	
	$: time = $mstime - start
	$: if ( time ) {
		rolodexComponent.nextItem()
	}
	
	




	const mstime = readable(new Date(), function start(set) {
		const interval = setInterval(() => {
			set(new Date());
		}, 7000);

		return function stop() {
			clearInterval(interval);
		};
});

	let rolodexComponent
	let index
</script>


<Rolodex bind:this={rolodexComponent}/>