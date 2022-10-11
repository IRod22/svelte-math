<script>
	/**
	 * @type {(count: number) => void}
	 */
	export let onchange
	let count = 0
	$: onchange(count)
</script>

<span class="counter">
	<button on:click={() => (count++)}>+</button>
	{count}
	<button on:click={() => (count--)}>-</button>
</span>