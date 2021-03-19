<template>
  <div>
    <p>(todoInput div)</p>
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>

    <modal v-if="showModal" @close="showModal=false">
      <input slot="header" type="text" v-model="newTodoItem" placeholder="할 일을 입력하세요." v-on:keyup.enter="addTodo">

      <ul slot="body">

      </ul>

      <span class="addContainer" v-on:click="addTodo">
        <i class="addBtn fas fa-plus" aria-hidden="true"></i>
      </span>
    </modal>
    <hr>
  </div>
</template>

<script>
  import Modal from './common/Modal.vue'
  export default {
    props: ['propsdata'],
    data() {
      return {
        newTodoItem: '',
        showModal: false
      }
    },

    methods: {
      addTodo() {
        if(this.newTodoItem != "") {
          var value = this.newTodoItem && this.newTodoItem.trim();
          this.$emit('addTodo', value);
          this.clearInput();
        }
        else {
          this.showModal = !this.showModal;
        }
      },

      clearInput() {
        this.newTodoItem = '';
      }
    },

    components: {
      Modal: Modal
    }
  }
</script>

<style>
</style>
