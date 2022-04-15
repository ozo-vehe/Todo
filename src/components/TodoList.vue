<template>
    <div class="todoList-container">
        <h2>Todo List</h2>
        <template v-for="todo in newTodoList" :key="todo.title">
            <div class="todo">
                <h3>{{ todo.title }}</h3>
                <p>{{ todo.place }}</p>
            </div>
        </template>
        <div class="todo-info">
            <p>completed <span>{{ completedTodo }}</span></p>
            <router-link >add</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoList',
    props: [
        'newTodoList'
    ],
    data() {
        return {
            todos: [
                {
                    category: 'business',
                    title: 'sketch workshop',
                    place: 'abuja',
                    time: '12pm',
                    notification: false
                },
                {
                    category: 'personal',
                    title: 'final design delivery',
                    place: 'lagos',
                    time: '10pm',
                    notification: true
                },
                {
                    category: 'business',
                    title: 'lunch run meeting',
                    place: 'port harcourt',
                    time: '1pm',
                    notification: false
                },
                {
                    category: 'business',
                    title: 'record techno mixtape',
                    place: 'nassarawa',
                    time: '10am',
                    notification: true
                },
                {
                    category: 'personal',
                    title: 'morning workout session',
                    place: 'kaduna',
                    time: '8am',
                    notification: true
                }
            ],
            completedTodo: 0,
            listCount: 0
        }
    },
}
</script>

<style scoped>
    .todoList-container {
        margin: 40px 3%;
        border: thin solid red;
    }
    .todoList-container h2 {
        text-decoration: capitalize;
        margin: 10px 0px 30px 0px;
    }
    .todo {
        padding: 5px 0px;
        margin: 20px 0px;
        text-transform: capitalize;
        transition: all 0.3s;
        cursor: pointer;
    }
    .todo:hover {
        background-color: #f0f5ff79;
    }
    .todo h3 {
        font-weight: 500;
        margin: 10px 0px;
    }
    .todo p {
        margin: 10px 0px 0px;
    }
    .todoList-container .todo-info {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .todo-info p {
        width: 50%;
        text-transform: capitalize;
    }
    .todo-info p span {
        border: thin solid red;
        border-radius: 50%;
        padding: 0.7% 1.2%;
    }
</style>