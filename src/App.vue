<script>
  export default {
    data() {
      return {
        todoText: '',
        todos: [
          {id:1, text:'장보기', checked: false, important: true},
          {id:2, text:'요리하기', checked: true, important: false},
        ]
      }
    }
  }
</script>

<template>
  <div class="container">
    <h1 class="text-center">To do List</h1>
    
    <div class="mb-3">
      <label for="todo" class="form-label">To do?</label>
      <input type="text" class="form-control" id="todo" placeholder="할일을 입력하세요">
    </div>

  </div>
</template>

<style scoped>

</style>