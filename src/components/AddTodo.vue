<template>
    <div>
        <form class="form" @submit="addTodo">
            <input type="text" placeholder="Add new todo..." class="input" v-model="title">
            <input type="text" placeholder="Id" class="input" v-model="id">
            <button type="submit"  class="input" >Add</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: "AddTodo",
        data(){
            return{
                title: '',
                id: ''
            }
        },
        methods:{
            addTodo(e){
                e.preventDefault();
                const newTodo = {
                    id : this.id,
                    title: this.title,
                    completed: false
                };
                this.$emit('add-Todo',newTodo);
                this.title = '';
            }
        }
    }
</script>

<style scoped>
    .form{
        display: flex;
        justify-content: center;
        align-items: center;
        height: 50px;
    }
    .input{
        margin-left: 10px;
    }
</style>