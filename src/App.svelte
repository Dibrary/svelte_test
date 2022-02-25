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

</script>

<div class="app">
    <TodoHeader/>
    <TodoInfo/>
    <TodoList {todos}/> <!--여기에 넣기만 한다고 화면에 나오지 않음, 해당 컴포넌트에서 코드를 구현해야됨.-->
</div>
