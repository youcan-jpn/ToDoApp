<template>
    <tr>
        <td>{{ todo.id }}</td>
        <td>{{ todo.text }}</td>
        <td>{{ addedDate }}</td>
        <td><input type="checkbox"></td>
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
    computed: {
        addedDate: function(){
            return this.todo.date.toLocaleString('ja')
        }
    }
}
</script>