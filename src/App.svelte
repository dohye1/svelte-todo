<script>
	import {todos} from './store'
	import Todo from './Todo.svelte';
	let title = "";
	let id = 0;

	function createTodo (){
		if(!title.trim()){
			title = '';
			return;
		}
		const newTodo = {
			id,
			title
		}
		$todos = [...$todos, newTodo];
		title = "";
		id++;
	}
</script>

<input 
	type="text" 
	bind:value={title} 
	on:keydown={(e)=>{
		if(e.key === "Enter"){
			createTodo()
		}	
	}}/>
<button on:click={createTodo}>
	Create Todo
</button>

{#each $todos as todo}
	<Todo {todo}/>
{/each}
