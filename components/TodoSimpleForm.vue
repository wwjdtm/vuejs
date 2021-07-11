<template>
  <!-- submit.prevent 리프레쉬하는 속성을 막음 -->
  <form @submit.prevent="onsubmit">
    <div class="d-flex">
      <div class="flex-grow-1 mr-2">
        <input
          class="form-control "
          type="text"
          v-model="todo"
          placeholder="Type new to-do"
        />
      </div>
      <div>
        <button class="btn btn-primary" type="submit">Add</button>
      </div>
    </div>

    <div v-show="hasError" style="color: red">field empty</div>
  </form>
</template>

<script>
import { ref } from 'vue';
export default {
  setup(props, context) {
    const todo = ref('');
    const hasError = ref(false);

    const onsubmit = () => {
      if (todo.value === '') {
        hasError.value = true;
      } else {
        // 이벤트 이름과 부모 컴포넌트로 보내는값
        context.emit('add-todo', {
          id: Date.now(),
          subject: todo.value,
          completed: false,
        });
        hasError.value = false;
        todo.value = '';
      }
    };
    return {
      todo,
      hasError,
      onsubmit,
    };
  },
};
</script>

<style></style>
