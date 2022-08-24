<script>
    let exampleList = ["item", "another item", "yet another item"];
    let exVal = "";
    let checked = false;

    let addItem = () => {
        exampleList = [...exampleList, exVal];
        exVal="";
    }

    let removeItem = (checkedItem) => {
        for (let i = 0 ; i < exampleList.length; i++) {
            if (exampleList[i] == checkedItem) {
                exampleList.splice(i, 1);
                exampleList = exampleList;
            }
        }
    }
</script>

<main>
    <h2>Todo</h2>
    
        <input type="text" placeholder="Add item" bind:value={exVal}/>
        <button on:click={addItem}> Add item</button>
    <form>
        {#each exampleList as example}
        <label>            
            <input type="checkbox" on:change={removeItem(example)} />
            {example}<br>
        </label>
        {/each}
    </form>
    
</main>

<style>
</style>