<script>
    /**
     * @type {string}
     */
    export let selected
    /**
     * @type {string[]}
     */
    export let options
</script>

<select bind:value={selected}>
    {#each options as option}
    <option value = {option}>{option}</option>
    {/each}
</select>