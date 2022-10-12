<script>
	/**
	 * @type {(count: number) => void}
	 */
	export let onchange
	let count = 0
	onchange(count)
	function incr() {
		count++
		onchange(count)
	}
	function decr() {
		count--
		onchange(count)
	}
</script>

<span class="counter">
	<button on:click={incr}>+</button>
	{count}
	<button on:click={decr}>-</button>
</span>