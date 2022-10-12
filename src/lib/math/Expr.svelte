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
     * @type {State[]}
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
    $: if (state == 'x') onchange(x => x)
</script>

<span>
    &lt;&lt;
{#if state == '#'}
    <Dropdown bind:selected = {state} options = {states}/> <Numeric onchange = {onchange}/>
{:else if state == '+' || state == '--' || state == '*' || state == '/'}
    <BinOp onchange = {onchange} op = {state == '+' ? ((a, b) => a + b) : state == '--' ? ((a, b) => a - b) : state == '*' ? ((a, b) => a * b) : ((a, b) => b == 0 ? 0 : a / b)}>
        <span slot="operator"><Dropdown bind:selected = {state} options = {states}/></span>
        <span slot="operand" let:onchange>
            <svelte:self onchange={onchange}></svelte:self>
        </span>
    </BinOp>
{:else}
    <Dropdown bind:selected = {state} options = {states}/>
{/if}
&gt;&gt;
</span>