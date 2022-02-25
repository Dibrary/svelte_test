<script>
    import TodoItem from './TodoItem.svelte';
    export let todos;
</script>

<div class="main">
    <ul>
        {#each todos as todo, index(todo)}
            <li>
                <TodoItem {todo}/>
            </li>
        {/each}
    </ul>
</div>