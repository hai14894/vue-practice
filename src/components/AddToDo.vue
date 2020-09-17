<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo ...">
            <input type="submit" value="submit" >
        </form>
    </div>
</template>


<script>

import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ""
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo =  {
                id: uuidv4(),
                title: this.title,
                completed:false
            }
            this.$emit('add-todo', newTodo);
            this.title = ''
            
            
        }
    }
}
</script>