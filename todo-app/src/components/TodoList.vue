<template>
    <div>
        <TodoInput
          v-model="newTodoText"
          placeholder="新しいTodoを入力"
          @keyup.enter="addTodo"
        />
        <table v-if="todos.length">
            <tr>
                <th>ID</th>
                <th>タスク</th>
                <th>追加された日時</th>
                <th>完了</th>
                <th>削除</th>
            </tr>
            <TodoListItem2
              v-for="todo in todos"
              :key="todo.id"
              :todo="todo"
              @remove="removeTodo"
            />
        </table>
        <p v-else>Todoリストに何も登録されていません．上の入力欄から新たなTodoを追加してください．</p>
    </div>
</template>

<script>
import TodoInput from './TodoInput.vue'
import TodoListItem2 from './TodoListItem2.vue'

let nextTodoId = 1

export default {
    components: {
        TodoInput, TodoListItem2
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