<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      },
    },
    methods: {
      toggleCheckbox(e) {
        // console.log(e.target.checked, this.todo.id)
        this.$emit('toggle-checkbox', { //부모로부터전달받은 ''안의 이름의 함수에게 인수 전달
          id: this.todo.id,
          check: e.target.checked
        })
      },
      clickDelete(e) {
        this.$emit('click-delete', this.todo.id);
      }
    }
}
</script>

<template>
  <div class="form-check" :data-id="todo.id">
    <input
      class="form-check-input" 
      type="checkbox" value="" 
      :id="'input'+todo.id"
      @change="toggleCheckbox"
    >
    <label 
      class="form-check-label" 
      :for="`input${todo.id}`"
      :style="todo.checked ? 'text-decoration:line-through':''"
    >
      {{ todo.text }}
    </label>
    <button type="button" @click="clickDelete">삭제</button>
  </div>
</template>

<style>
  button{
    margin-left: 10px;
    border:none;
    background-color: transparent;
    color: #ccc;
    transition: 0.3s ease-in;
  }
  button:hover{
    color: #000;
    background-color: #ccc;
  }
</style>