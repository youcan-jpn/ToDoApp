<template>
    <tr>
        <td>{{ todo.id }}</td>
        <td>{{ todo.text }}</td>
        <td>{{ addedDateFormatted }}</td>
        <td><input type="checkbox" v-model="completed">{{ judgeCompleted(completed) }}</td>
        <td></td>
        <td>
          <button @click="$emit('remove', todo.id)">
          削除する
          </button>
        </td>
    </tr>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            completed: false,
        }
    },
    computed: {
        addedDateFormatted: function(){
            return this.todo.addedDate.toLocaleString('ja')
        }
    },
    methods: {
        judgeCompleted: function(c){
            if(c) {
                return "完了済"
            } else {
                return "未完了"
            }
        }
    }
}
</script>