<template>
  <div>
      <span>
        <button v-on:click="cleatTodo">Clear All</button>
      </span>
  </div>
</template>

<script>
export default {
  methods: {
    cleatTodo: function () {
      localStorage.clear();
    }
  }
}
</script>

<style>

</style>