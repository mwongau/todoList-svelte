<script>
let id = 0
let newItem = $state('')
let items = $state([])
	
function addItem(evt) {
    if (evt.key === 'Enter') {
        if (newItem.trim() !== '') {
        items.push({id:id++, item: newItem})
        newItem = ''	  }
    }
}

function removeItem(todo) {
    items = items.filter((t) => t !== todo)
}

function clickHandler() {
    if (newItem.trim() !== '') {
        items.push({id:id++, item: newItem})
        newItem = ''
    }
}
</script>

<h3> To-Do list implemeted by Svelte 5 and SvelteKit</h3>

<input class="myinput" type="text" bind:value={newItem} onkeydown={addItem} /> 
<button class="mybutton" onclick= {clickHandler}>Add</button>
{#if items.length === 0}
<p>Todo list is empty. Please add todo item.</p>
{/if}
<h4> To-Do list: </h4>
<ul>
{#each items as todo (todo.id)}
   <li>
      { todo.item }
      <button class="mybutton" onclick={()=>removeItem(todo)}>Delete</button>
   </li>
{/each}
</ul>

<style>
.myinput {
  width: 200px;
  padding: 5px;
  
}

.mybutton {
  background-color: lightblue;
  padding: 3px;
  margin: 3px;
}
</style>
