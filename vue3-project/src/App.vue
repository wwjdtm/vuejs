<template>
  <div class="container">
    <h2>To-Do List</h2>
    <TodoSimpleForm @add-todo="addTodo" />

    <div v-if="!todos.length">추가된 todo 가 없습니다</div>
    <!-- props로 보내는 이름을 적고 데이터명 적음 -->
    <!-- 자식 컴포넌트에서는 앞의 이름으로 뒤의 데이터에 접근가능 -->
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import { ref } from 'vue';
import TodoSimpleForm from '@/components/TodoSimpleForm.vue';
import TodoList from '@/components/TodoList.vue';

export default {
  components: {
    TodoSimpleForm,
    TodoList,
  },
  setup() {
    const todos = ref([
      // {id : 1, subject : 'ee'}
    ]);

    const todoStyle = {
      textDecoration: 'line-through',
      color: 'gray',
    };

    const addTodo = (todo) => {
      todos.value.push(todo);
    };

    const deleteTodo = (index) => {
      todos.value.splice(index, 1);
    };

    return {
      addTodo,
      todos,
      todoStyle,
      deleteTodo,
    };
  },
};
</script>

<style></style>
