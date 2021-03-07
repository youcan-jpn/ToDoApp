<template>
    <li>
        {{ todo.text }} ({{ todo.date.toLocaleString('ja') }}に追加されました)
        <button @click="$emit('remove', todo.id)">
            完了にする
        </button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    }
}
</script>

<style>
li:hover{
    color: #42b983;
}
</style>