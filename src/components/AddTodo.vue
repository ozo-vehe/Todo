<template>
    <div class="addTodo-container">
        <div class="addTodoHeader">
            <h2>add todo</h2>
        </div>

        <form class="todoInput">
            <select v-model="todoInput.category" name="category" id="category">
                <option value="business">business</option>
                <option value="personal">personal</option>
            </select>
            <input v-model.lazy="todoInput.title" type="text" name="title" id="title" placeholder="title">
            <input v-model.lazy="todoInput.place" type="text" name="place" id="place" placeholder="place">
            <input v-model.lazy="todoInput.time" type="text" name="time" id="time" placeholder="time">
            <button @click.prevent="$emit('submitTodo', todoInput)">Add Todo</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            todoInput:  {
                category: null,
                title: null,
                place: null,
                time: null
            }
        }
    },
    // methods: {
    //     submitTodo () {
    //         console.log(this.todoInput)
    //     }
    // },
    emits: ['submitTodo']
}
</script>

<style scoped>
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