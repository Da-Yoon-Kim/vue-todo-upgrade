<template>
  <div>
    <p>(todoList div)</p>
    <section>
      <ul>
        <p v-if="flag">해야 할 일이 없습니다.</p>
      </ul>
    </section>
    <hr>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        todoItems: [],
        flag: ''
      }
    },

    created() {
      if(localStorage.length==1 && localStorage.key(0)=="loglevel:webpack-dev-server") {
        this.flag = true;
      }
      else if(localStorage.length > 0) {
        if (localStorage.key(i) != "loglevel:webpack-dev-server") {
          this.todoItems.push(localStorage.key(i));
        }
        this.flag = false;
      }
      else {
        this.flag = true;
      }
    }
  }
</script>

<style>
</style>
