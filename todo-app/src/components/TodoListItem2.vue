<template>
    <tr>
        <td>{{ todo.id }}</td>
        <td>{{ todo.text }}</td>
        <td>{{ addedDateFormatted }}</td>
        <td><input type="checkbox" v-model="completed" @change="$emit('change', completed, todo)">
          <span v-if="completed">済</span>
          <span v-else>未完了</span>
        </td>
        <td>{{ completedDateFormatted }}</td>
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
        },
        completedDateFormatted: function(){
            return this.todo.completedDate.toLocaleString('ja')
        }
    }
}
</script>