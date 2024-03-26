<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>


<script> import '../style.css'
let todoItem = '';
//let urgeent, someday;
let todoList = [];
function addToArray() {
     if(todoItem==''){
          return;
     }
     todoList = [ ...todoList,{
          text: todoItem,
          done: false
     }]
     console.log(todoList);
     todoItem = '';
}
function removeThis(index){
     todoList.splice(index,1);
}
</script>
<h1>To do</h1>
<form on:submit={addToArray}>
     <input type="text" bind:value={todoItem}>
<input type="Submit"><button> Add </button>
</form>
<ul>
     {#each todoList as item, index}
 <li>
<input type="checkbox" bind:checked={item.done}>
<span class.done={item.done}>{item.text}</span>
     <span on:click={() => removeThis(index)}
          class="remove" role="button" tabindex="0">&items;
</span>
</li>

{/each}
</ul>
<style>
     ul{
          list-style: none;
     }
     .done{
          color:aquamarine;
          text-decoration: line-through;
     }
     .remove{
          color:rgb(113, 6, 58);
     }
</style>