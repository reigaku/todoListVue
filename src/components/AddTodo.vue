<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">create</button>
    </form>
</template>

<script>
export default{
    data(){
        return {
            title: ''
        }
    },
    methods: {
        onSubmit(){
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }
}
</script>


<style scoped>
    input{
        border: 1px solid #ccc;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        margin-right: 1rem;
    }

    button{
        background: green;
        color: white;
        border: 1px solid #ccc;
        padding: .5rem 2rem;
        
    }
</style>