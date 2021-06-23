<template>
    <div class="container">

        <h2>To-Do List</h2>
        <!-- submit.prevent 리프레쉬하는 속성을 막음 -->
        <form @submit.prevent = "onsubmit" >
            <div class="d-flex">
                <div class="flex-grow-1 mr-2">
                    <input class = "form-control " type="text" v-model="todo" placeholder="Type new to-do">
                </div>
                <div>
                    <button class="btn btn-primary" type = "submit">Add</button>
                </div>

            </div>
            

            <div v-show="hasError" style="color: red">field empty</div>
           
           
            
        </form>
        <div v-if="!todos.length">추가된 todo 가 없습니다</div>
        <!-- v-for 사용하려면 고유값 있어야됨 .-> key : todo id -->
        <div v-for = "(todo, index) in todos" class="card mt-2" :key="todo.id">
            <div class="card-body p-2 d-flex align-items-center">
                <div class = "form-check flex-grow-1">
                    <input class = "form-check-input" type="checkbox" v-model="todo.completed">
                    <label class = "form-check-label" :style="todo.completed ? todoStyle : {}" > {{ todo.subject }}</label>
                </div>

                <div>
                    <button class = "btn btn-danger btn-sm"
                    @click = "deleteTodo(index)"> Delete</button>
                </div>
              

            </div>

        </div>
    </div>
    
</template>

<script>
import { ref } from 'vue';

export default({
    setup() {
        const todo = ref('');
        const todos = ref([
            // {id : 1, subject : 'ee'}
            ]);

        const hasError = ref(false);
        const todoStyle = {
            textDecoration : 'line-through',
            color : 'gray'
        }


        const onsubmit = () => {
            if ( todo.value ===''){
                hasError.value = true;
            } else {
                
                todos.value.push({
                id : Date.now(),
                subject : todo.value,
                completed : false
            });
            hasError.value = false;
            todo.value = '';

            }
            
        }

        const deleteTodo = (index) => {
            todos.value.splice(index, 1);
        }
    
        return {
            todo,
            onsubmit,
            todos,
            hasError,
            todoStyle,
            deleteTodo
        };
    },
    
})
</script>

<style>

</style>
