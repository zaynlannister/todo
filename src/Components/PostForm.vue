<template>
  <div class="todo__action">
    <input v-model="inputValue" class="input default-border" type="text" placeholder="Enter task">
    <button @click="addTask" class="btn">SUBMIT</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: "",
    }
  },

  methods: {
    addTask() {
      if (this.inputValue.length === 0) return;
      const task = {
        id: Date.now(),
        status: "to-do",
        title: this.inputValue
      }
      this.$emit("create", task);

      this.inputValue = "";
    }
  }
}
</script>

<style scoped>

</style>