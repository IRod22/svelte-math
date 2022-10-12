<script>
    /**
     * @type {(a: number, b: number) => number}
     */
    export let op
    /**
	 * @type {(fn: (x: number) => number) => void}
	 */
	export let onchange

    /**
     * @param {(x: number) => number} a
     * @param {(x: number) => number} b
     * @returns {(x: number) => number}
     */
    function funOp(a, b) {
        return x => op(a(x), b(x))
    }

    /**
     * @param {number} x
     */
    let a = x => x
    /**
     * @param {number} x
     */
    let b = x => x

    /**
     * @param {(x: number) => number} newA
     */
    function setA(newA) {
        a = newA
        onchange(funOp(a, b))
    }
    /**
     * @param {(x: number) => number} newB
     */
    function setB(newB) {
        b = newB
        onchange(funOp(a, b))
    }
</script>

<span>
    <slot name = "operand" onchange = {setA}></slot>
    <slot name = "operator"></slot>
    <slot name = "operand" onchange = {setB}></slot>
</span>