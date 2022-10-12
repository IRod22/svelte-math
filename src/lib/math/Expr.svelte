<script>
    import Numeric from "./Numeric.svelte"
    import BinOp from "./BinOp.svelte"
    import Dropdown from "$lib/Dropdown.svelte";
    /**
     * @typedef {'x'|'#'|'+'|'--'|'*'|'/'} State
    */
    /**
	 * @type {(fn: (x: number) => number) => void}
	 */
	export let onchange
    /**
     * @type {string[]}
     */
    const states = [
        'x',
        '#',
        '+',
        '--',
        '*',
        '/',
    ]
    let state = 'x'
    const updateIfX = () => {if (state == 'x') onchange(x => x)}
    /**
     * @param {string} newState
     */
    const updateState = newState => {
        state = newState
        updateIfX()
    }
</script>

<span>
    &lt;&lt;
{#if state == '#'}
    <Dropdown selected = {state} select = {updateState} options = {states}/> <Numeric onchange = {onchange}/>
{:else if state == '+' || state == '--' || state == '*' || state == '/'}
    <BinOp onchange = {onchange} op = {state == '+' ? ((a, b) => a + b) : state == '--' ? ((a, b) => a - b) : state == '*' ? ((a, b) => a * b) : ((a, b) => b == 0 ? 0 : a / b)}>
        <span slot="operator"><Dropdown selected = {state} select = {updateState} options = {states}/></span>
        <span slot="operand" let:onchange>
            <svelte:self onchange={onchange}></svelte:self>
        </span>
    </BinOp>
{:else}
    <Dropdown selected = {state} select = {updateState} options = {states}/>
{/if}
&gt;&gt;
</span>