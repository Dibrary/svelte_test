<script>
    import TodoItem from './TodoItem.svelte';
    export let todos;
    export let handleCheckTodo;
    export let handleRemoveTodo;
    export let editMode;
    export let handleChangeEditMode;
    export let handleEditTodoItem;
</script>

<div class="main">
    <ul>
        {#each todos as todo, index(todo)}
            <li>
                <TodoItem {todo}{handleCheckTodo}{handleRemoveTodo}{editMode}{handleChangeEditMode}{handleEditTodoItem}/>
            </li>
        {/each}
    </ul>
</div>

