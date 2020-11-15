<template>
    <div>
        <ul>
            <TodoItem v-for = "(item, i) in todos" 
            @delete-todo="deleteTodo"
            :todo="item" 
            :index="i"
            :key="i"></TodoItem>
        </ul>
    </div>
</template>

<script>
    import TodoItem from '@/components/TodoItem';
    export default {
        props: ['todos'],
        components: {
            TodoItem
        },
        methods:{
            deleteTodo(id){
                this.$emit('delete-todo', id)
            }
        }
    };
</script>

<style scoped>
    ul{
        list-style:none;
        margin:10px auto;
        padding:0;
        text-align: left;
    }
</style>