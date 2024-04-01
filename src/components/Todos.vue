<template>
    <div class="columns is-multiline">
        <div class="column is-6 is-offset-3">
            <div class="box">
                <form @submit.prevent="onSubmit">
                    <div class="field">
                         <label class="label">Add your Todo</label>
                         <div class="control">
                            <input class="input" type="text" placeholder="Enter your Todods.." v-model="title"/>
                         </div>
                    </div>
                </form>
            </div>
        </div>
        <div class="column is-6 is-offset-3" v-for="todo in todos" :key="todo.id">
         <div class="box todo_box" @click="$emit('onComplete', todo.id)">
            <span :class="{completed:todo.completed}">{{ todo.title }}</span>
             <button class="button is-danger is-small is-pulled-right"  v-if="todo.completed" @click="$emit('onDelete', todo.id)">Delete</button>
        </div>
        </div>
    </div>
</template>

<script>
import shortid from "shortid"
export default {
    name: "TodosList",
    props: ["todos"],
    data(){
        return{
            title: ""
        }
    },

    methods: {
        onSubmit(){
            const new_todo = {
                title: this.title,
                completed: false,
                id: shortid.generate(),
            };
            this.$emit("addTodo", new_todo)
            this.title=""
        }
    },

};
</script>
<style>
.completed{
    text-decoration: line-through;
}
.todo_box{
  transition: all;
}
.todo_box:hover {
    cursor: pointer;
    background-color: #f0f3bd;
    transform: scale(1.1);
}

</style>