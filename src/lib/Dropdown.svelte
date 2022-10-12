<script>
    /**
     * @type {string}
     */
    export let selected
    /**
     * @type {(selected: string) => void}
    */
    export let select
    /**
     * @type {string[]}
     */
    export let options
    $: select(selected)
</script>

<select bind:value={selected}>
    {#each options as option}
    <option value = {option}>{option}</option>
    {/each}
</select>