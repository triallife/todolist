<script>
  import Todo from './components/Todo.vue';

  export default {
    data() {
      return {
        todoText: '',
        todos: [
          {id:1, text:'장보기', checked: false},
          {id:2, text:'요리하기', checked: false},
        ]
      }
  },
  components: {
    Todo
  },
  methods: {
    AddTodo(e) {
      this.todos.push({
        id:Math.random(), text:e.target.value, checked: false
      })
      this.todoText = '';
    },
    toggleCheck({ id, check }) {
      const index = this.todos.findIndex(todo => todo.id === id);
      this.todos[index].checked = check;
      console.log(this.todos);
    },
    clickDelete(id) {
      if (window.confirm('정말 삭제할까요?')) {
        const index = this.todos.findIndex(todo => todo.id === id);
        this.todos.splice(index, 1);
      } else {
        alert('취소했습니다');
      }
    }
  }
    
  }
</script>

<template>
  <div class="container">
    <h1 class="text-center">To do List</h1>
    
    <div class="mb-3">
      <label for="todo" class="form-label">To do?</label>
      <input 
        type="text" 
        class="form-control" 
        id="todo" 
        placeholder="할일을 입력하세요"
        required
        @keyup.enter="AddTodo"
        v-model="todoText"
      >
    </div>
    <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-checkbox="toggleCheck"
      @click-delete="clickDelete"
    >
    </Todo>

  </div>
</template>

<style scoped>

</style>