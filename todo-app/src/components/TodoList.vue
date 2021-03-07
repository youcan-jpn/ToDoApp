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
                <th>完了された日時</th>
                <th>削除</th>
            </tr>
            <TodoListItem2
              v-for="todo in todos"
              :key="todo.id"
              :todo="todo"
              @remove="removeTodo"
              @change="completeTodo"
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
                    addedDate: new Date(2021, 2, 5, 9, 12, 53),
                    completedDate: new Date(2021, 2, 5, 13, 4, 24)
                },
                {
                    id: nextTodoId++,
                    text: 'ハンドボールを練習する',
                    addedDate: new Date(2021, 2, 6, 10, 23, 2),
                    completedDate: new Date(2021, 2, 6, 21, 43, 24)
                },
                {
                    id: nextTodoId++,
                    text: '数学2Dの予習をする',
                    addedDate: new Date(2021, 2, 7, 11, 56, 23),
                    completedDate: ""
                }
            ]
        }
    },

    methods: {
        addTodo() {
            const trimmedText = this.newTodoText.trim()
            if (trimmedText) {
                var addedDate = new Date()
                this.todos.push({
                    id: nextTodoId++,
                    text: trimmedText,
                    addedDate: addedDate,
                    completedDate: ""
                })
                this.newTodoText = ''
            }
        },
        removeTodo(idToRemove) {
            this.todos = this.todos.filter(todo => {
                return todo.id !== idToRemove
            })
        },
        completeTodo(completed, ToChange){
            if (completed){
            /* unchecked -> checked の変更の場合はタスクが完了した時刻を今の時刻に設定する */
                ToChange.completedDate = new Date()
            } else {
            /* checked -> unchecked の変更の場合はタスクが未完了に戻されたということなので完了時刻を表示しないようにから文字列に設定する*/
                ToChange.completedDate = ""
            }
        }
    }
}
</script>