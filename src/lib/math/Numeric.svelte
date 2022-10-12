<script>
    import Counter from '$lib/Counter.svelte'

    /**
	 * @type {(fn: (x: number) => number) => void}
	 */
	export let onchange

    /**
     * @param {number} number
     * @returns {(x: number) => number}
     */
    function toCb(number) {
        return () => number
    }
</script>

<Counter onchange = {ctr => onchange(toCb(ctr))}></Counter>