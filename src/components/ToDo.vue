<template>
  <input 
  type="text"
  placeholder="Enter todo and hit enter"
  class="border-orange-300 border-2 w-full p-2 rounded"
  v-model="todoTitle"
  @keyup.enter="addToDo"
  >
  <div class="mt-4">
    <div v-for="(todo, index) in todos" :key="index" class="flex border-gray-300 border-b-2 mb-2 p-1">
      <div class="w-5/6 text-lg" :class="{'line-through text-green-600':todo.complete}">{{todo.title}}</div>
      <div class="w-1/6 flex">
        <div class="mr-4">
          <button 
          class="bg-red-500 text-white text-xs font-bold px-2 rounded cursor-pointer hover: bg-red-600"
          @click="deleteTodo(index)"
          >X</button>
        </div>
        <div>
          <input 
          type="checkbox" 
          :checked="todo.complete"
          @click="toggleTodo(index)"
          >
        </div>

      </div>
    </div>
  </div>
  <div v-if="todos.length == 0">
    <div class="text-2xl font-bold">Your ToDo list is empty</div>
  </div>
</template>

<script>
import { ref } from "vue"
export default {
  setup() {
    var todoTitle = ref("")
    const todos = ref([])
    function addToDo() {
      this.todos.push({ title: this.todoTitle, complete: false})
      this.todoTitle = ""
    }
    function toggleTodo(index) {
      this.todos[index].complete = !this.todos[index].complete
    }
    function deleteTodo(index) {
      this.todos.splice(index, 1)
    }
    return { todoTitle, todos, addToDo, toggleTodo, deleteTodo}
  }
}
</script>


<style></style>