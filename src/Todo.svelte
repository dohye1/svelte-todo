<script>
	import {todos} from './store'
    export let todo;
    let title = '';
    let isEdit = false;

    function updateTodo(){
        todo.title = title;
        offEdit();
    }
    function offEdit(){
        isEdit=false;
    }
    function onEdit () {
        isEdit = true;
        title = todo.title;
    }

    function onDelete () {
        $todos = $todos.filter(t=>t.id !== todo.id)
    }
</script>

{#if isEdit}
    <div>
        <input type="text" bind:value={title} on:keydown={(e)=>{e.key==="Enter" && updateTodo()}}/>
        <button on:click={updateTodo}>OK</button>
        <button on:click={offEdit}>Cancel</button>
    </div>
{:else}
    <div>
        {todo.title}
        <button on:click={onEdit}>Edit</button>
        <button on:click={onDelete}>Delete</button>
    </div>
{/if}