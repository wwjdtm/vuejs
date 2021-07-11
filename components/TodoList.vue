<template>
  <!-- v-for 사용하려면 고유값 있어야됨 .-> key : todo id -->
  <!-- todo 는 app.vue 에서 관리하므로 props 로 받아와야함 -->
  <div v-for="(todo, index) in todos" class="card mt-2" :key="todo.id">
    <div class="card-body p-2 d-flex align-items-center">
      <div class="form-check flex-grow-1">
        <input
          class="form-check-input"
          type="checkbox"
          v-model="todo.completed"
        />
        <label
          class="form-check-label"
          :style="todo.completed ? todoStyle : {}"
        >
          {{ todo.subject }}</label
        >
      </div>

      <div>
        <button class="btn btn-danger btn-sm" @click="deleteTodo(index)">
          Delete
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // 부모에서 보낸 props의 앞의 이름을적음, 위의 템플릿에서 바로 적용가능
  // props: ['todos'], 아래처럼 타입, requried 작성가능
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style></style>
