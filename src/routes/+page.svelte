<script>
    import Counter from "$lib/Counter.svelte";
    import Expr from "$lib/math/Expr.svelte";
    let x = 0
    /**
     * @param {number} x
     */
    let f = x => x
    $: y = f(x)
</script>

<p>Where x = <Counter onchange = {newX => (x = newX)}/>, y = <Expr onchange = {newF => (f = newF)}/> = {y}</p>