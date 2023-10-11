<template>
  <div class="content">
    <h1>Intro to vue 3</h1>
    <form @submit.prevent="addTodo">
      <div class="field">
        <label class="label">Todo</label>
        <div class="control">
          <input
            v-model="todo"
            type="text"
            class="input"
            placeholder="Todo gir"
          />
        </div>
      </div>
      <button type="submit" class="button is-warning">Ekle</button>
    </form>
    <div v-for="todo in todos" :key="todo.id" class="card my-5 mx5">
      <div class="card-content">
        <div class="media">
          <div class="media-content">
            <p
              :class="{ done: todo.done }"
              @click="done(todo)"
              class="title is-4 cursor"
            >
              {{ todo.content }}
            </p>
            <p class="subtitle is-6">{{ todo.done }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const todo = ref("");
    const todos = ref([]);

    function addTodo() {
      todos.value.push({
        done: false,
        content: todo.value,
        id: Date.now(),
      });
      todo.value = "";
    }
    function done(todo) {
      todo.done = !todo.done;
    }

    return {
      todo,
      todos,
      addTodo,
      done,
    };
  },
};
</script>
<style lang="scss">
.done {
  text-decoration: line-through;
}
.cursor {
  cursor: pointer;
}
</style>
