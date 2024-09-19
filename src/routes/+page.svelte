<script>
let newItem = $state('')
let items = $state(['Buy apples', 'Buy oranges', 'Buy bananas'])
	
function addItem(evt) {
    if (evt.key === 'Enter') {
      items = [...items, newItem];
      newItem = '';
    }
}

function removeItem(item) {
  items = items.filter((t) => t !== item)
}
</script>

<h3> To-Do list implemeted by Svelte </h3>
<h4> Enter new item in text box, then presss Enter key to add it to To-Do list. 
Click the Delete button to delete the selected item from To-Do list.</h4>
<input type="text" bind:value={newItem} onkeydown={addItem} /> 
<h4> To-Do list: </h4>
<ul>
{#each items as item}
   <li>
      { item }
      <button onclick={removeItem(item)}>Delete</button>
   </li>
{/each}
</ul>
