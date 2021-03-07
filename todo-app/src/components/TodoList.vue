<template>
    <div>
        <TodoInput
          v-model="newTodoText"
          placeholder="新しいTodoを入力"
          @keyup.enter="addTodo"
        />
        <ul v-if="todos.length">
            <TodoListItem
              v-for="todo in todos"
              :key="todo.id"
              :todo="todo"
              @remove="removeTodo"
            />
        </ul>
        <p v-else>Todoリストに何も登録されていません．上の入力欄から新たなTodoを追加してください．</p>
    </div>
</template>

<script>
import TodoInput from './TodoInput.vue'
import TodoListItem from './TodoListItem.vue'

let nextTodoId = 1

export default {
    components: {
        TodoInput, TodoListItem
    },

    data () {
        return {
            newTodoText: '',
            todos: [
                {
                    id: nextTodoId++,
                    text: 'Vue.jsを勉強する',
                    date: new Date(2021, 2, 5, 9, 12, 53)
                },
                {
                    id: nextTodoId++,
                    text: 'ハンドボールを練習する',
                    date: new Date(2021, 2, 6, 10, 23, 2)
                },
                {
                    id: nextTodoId++,
                    text: '数学2Dの予習をする',
                    date: new Date(2021, 2, 7, 11, 56, 23)
                }
            ]
        }
    },

    methods: {
        addTodo() {
            const trimmedText = this.newTodoText.trim()
            if (trimmedText) {
                var date = new Date()
                this.todos.push({
                    id: nextTodoId++,
                    text: trimmedText,
                    date: date
                })
                this.newTodoText = ''
            }
        },
        removeTodo(idToRemove) {
            this.todos = this.todos.filter(todo => {
                return todo.id !== idToRemove
            })
        }
    }
}
</script>