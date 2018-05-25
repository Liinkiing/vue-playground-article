<template>
    <div id="app" class="App">
        <p class="my-component">
            Je suis mon premier composant
        </p>
        <ul>
            <li v-for="todo in todos" :key="todo.id">
                {{ todo.name }} - {{ todo.dueDate.toLocaleString() }}
            </li>
        </ul>
        <input type="text" v-model="newTodo" @keyup.enter="addTodo" placeholder="Entrez votre todo...">
    </div>
</template>

<style lang="scss">
    li {
        font-size: 2rem;
        color: red;
        &:hover {
            color: blue;
        }
    }
</style>

<script>
    export default {
        name: 'app',
        methods: {
            addTodo () {
                if (this.newTodo === '') return
                const id = this.todos[this.todos.length - 1].id + 1
                const todo = {
                    id,
                    name: this.newTodo,
                    dueDate: new Date()
                };
                this.todos.push(todo)
                this.newTodo = ''
            }
        },
        data () {
            return {
                newTodo: '',
                todos: [
                    {
                        id: 1,
                        name: 'Todo 1',
                        dueDate: new Date()
                    },
                    {
                        id: 2,
                        name: 'Todo 2',
                        dueDate: new Date()
                    },
                    {
                        id: 3,
                        name: 'Todo 3',
                        dueDate: new Date()
                    },
                    {
                        id: 4,
                        name: 'Todo 4',
                        dueDate: new Date()
                    }
                ]
            }
        }
    }
</script>
