<script>
// @ts-nocheck

	import { writable } from 'svelte/store'
	/**
	 * @type {(count: number) => void}
	 */
	export let onchange
	let count = writable(0)
	count.subscribe(() => {
		onchange($count)
	})
</script>

<span class="counter">
	<button on:click={() => $count++}>+</button>
	{$count}
	<button on:click={() => $count--}>-</button>
</span>