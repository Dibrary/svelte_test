<script>
    import TodoHeader from './components/TodoHeader.svelte';
    import TodoInfo from './components/TodoInfo.svelte';
    import TodoList from './components/TodoList.svelte';
    import {v4 as uuid} from 'uuid';
    let todos = [
        {
            id:1,
            content:'첫 번째 할일',
            done:false
        },
        {
            id:2,
            content:'두 번째 할일',
            done:false
        },
        {
            id:3,
            content:'세 번째 할일',
            done:true
        },
        {
            id:4,
            content:'네 번째 할일',
            done:false
        }
    ]
    function handleCheckTodo(id) {
        todos = todos.map(todo => {
            if(todo.id === id){
                todo.done = !todo.done;
            }
            return todo;
        })
    }
    let todoValue = '';
    function addTodoItem() {
        if(todoValue) {
            const newTodo = {
                id:uuid(),
                content:todoValue,
                done:false,
            }
        todos = [...todos, newTodo];
        todoValue = '';
        }
    }
    function handleTodoInputKeyup(e) {
        if(e.keyCode === 13) {
            editTodoItem(editTodo);
            // console.log(`todoValue:${e.target.value}`)
            // todoValue = e.target.value;
            // addTodoItem();
        }
    }
    function handleRemoveTodo(id) {
        todos = todos.filter(todo => todo.id !== id);
    }
    let editMode='';
    function handleChangeEditMode(id) {
        editMode=id;
    }
    function closeEditMode() {
        editMode='';
    }
    function handleEditTodoItem(e, editTodo) {
        if(e.key===13){
            editTodoItem(editTodo);
        }
    }
    function editTodoItem(editTodo) {
        todos = todos.map(todo => {
            if(todo.id === editTodo.id) {
                todo = editTodo
            }
            return todo;
        })
        closeEditMode();
    }

    $: todoCount = todos.length;

</script>

<div class="app">
    <TodoHeader {todoValue} {handleTodoInputKeyup}/>
    <TodoInfo {todoCount}/>
    <TodoList {todos}{handleCheckTodo}{handleRemoveTodo}{editMode}{handleChangeEditMode}{handleEditTodoItem}/> <!--여기에 넣기만 한다고 화면에 나오지 않음, 해당 컴포넌트에서 코드를 구현해야됨.-->
</div>
