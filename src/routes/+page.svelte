<script>
let id = 0
let newItem = $state('')
let items = $state([])
	
function addItem(evt) {
    if (evt.key === 'Enter') {
	  items.push({id:id++, item: newItem})
	  items = items
      newItem = '';
    }
}

function removeItem(todo) {
    items = items.filter((t) => t !== todo)
}

function clickHandler() {
    items.push({id:id++, item: newItem})
    items = items
    newItem = ''
}
</script>

<h3> To-Do list implemeted by Svelte </h3>
<h4> Enter new item in text box, then presss Enter key to add it to To-Do list. 
Click the Delete button to delete the selected item from To-Do list.</h4>
<input type="text" bind:value={newItem} onkeydown={addItem} /> 
<button onclick= {clickHandler}>Add</button>
{#if items.length === 0}
<p>Todo list is empty. Please add todo item.</p>
{/if}
<h4> To-Do list: </h4>
<ul>
{#each items as todo (todo.id)}
   <li>
      { todo.item }
      <button onclick={removeItem(todo)}>Delete</button>
   </li>
{/each}
</ul>
