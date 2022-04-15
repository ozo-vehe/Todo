<template>
    <div class="headerComponent-container">
        <div class="todo-title">
            <h2 class="header-title">Hello, {{ name }} <br> welcome back</h2>
            <p class="curr-date">{{ currentDate }}</p>
        </div>

        <div class="todo-sum">
            <div class="personal">
                <h2 class="personal-count">{{ personalCount }}</h2>
                <p>personal</p>
            </div>

            <div class="business">
                <h2 class="business-count">{{ businessCount }}</h2>
                <p>business</p>
            </div>
        </div>
    </div>

    <div class="todoList-container">
        <h2>Todo List</h2>
        <template v-for="todo in todos" :key="todo.title">
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

    <div class="addTodo-container">
        <div class="addTodoHeader">
            <h2>add todo</h2>
        </div>

        <form class="todoInput">
        </form>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'TodoApp',
    // props: [ 'name' ],
    data() {
        return {
            businessCount: 0,
            personalCount: 0,
            currentDate: null,
            months: [
                'jan',
                'feb',
                'mar',
                'apr',
                'may',
                'jun',
                'jul',
                'aug',
                'sep',
                'oct',
                'nov',
                'dec'
            ],
            todos: [],
            completedTodo: 0,
            listCount: 0
        }
    },
    methods: {
        changeNumber() {
            this.personalCount = 20
        },
        getDate () {
            let newCurrentDate = new Date
            let month = newCurrentDate.getMonth()
            let date = newCurrentDate.getDate()
            let year = newCurrentDate.getFullYear()

            this.currentDate = `${this.months[month]} ${date}, ${year}`
        },
        getPost () {
            axios.get('https://jsonplaceholder.typicode.com/posts')
                .then((res) => {
                    console.log(res.data)
                })
                .catch((err) => {
                    consloe.log(err)
                })
        }
    },
    mounted () {
        this.getDate()
        this.getPost()
    }
}
</script>

<style scoped>
    .headerComponent-container {
        color: #ffffff;
        background-image: url('../assets/bg.jpg');
        background-position: center;
        background-size: cover;
        width: 100%;
        height: 100vh;
        display: flex;
        justify-content: space-between;
    }
    .headerComponent-container .todo-title {
        width: 65%;
        padding: 10%;
        box-sizing: border-box;
        display: flex;
        align-items: flex-start;
        justify-content: center;
        flex-direction: column;
    }
    .todo-title h2 {
        font-size: 4.1rem;
        line-height: 1.5;
        font-weight: 600;
        text-transform: capitalize;
    } 
    .todo-title p {
        font-size: 1.5rem;
        text-transform: capitalize;
    }
    .headerComponent-container .todo-sum {
        box-sizing: border-box;
        width: 35%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        background-color: #00000060;
    }
    .todo-sum div {
        width: 50%;
        text-transform: capitalize;
        text-align: center;
    }
    .todo-sum div h2 {
        font-size: 3rem;
        margin: 0px;
    }
    .todo-sum div p {
        margin: 5px;
    }

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

    .addTodoHeader {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .addTodoHeader h2 {
        text-transform: capitalize;
    }

    form {
        display: flex;
        flex-direction: column;
        padding: 10px 3%;
        box-sizing: border-box;
    }
    form * {
        margin: 10px 0px;
    }
    form input,
    form button,
    form select{
        outline: none;
        background: none;
        height: 35px;
        font-size: 16px;
        border: none;
        border-bottom: thin solid #d4d3d3;
        text-transform: capitalize;
    }
    select option {
        border: thin solid red;
    }
    form input {
        padding-left: 10px;
    }
    form button {
        background-color: #114992c2;
        color: #fff;
        border: none;
        height: 40px;
        cursor: pointer;
        transition: all 0.3s;
    }
    form button:hover {
        background-color: #114992ef;
    }
</style>