<template>
  <div class="todo__action">
    <input
        :value="modelValue"
        v-on:keydown.enter="addTask"
        class="input default-border"
        type="text"
        placeholder="Enter task"
        @input="$emit('update:modelValue', $event.target.value)"
    >
    <button @click="addTask" class="btn">SUBMIT</button>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String
  },

  methods: {
    isValid() {
      return this.modelValue.length !== 0;
    },

    addTask() {
      if (this.isValid()) {
        this.$emit("create", {
          id: Date.now(),
          status: "to-do",
          title: this.modelValue
        });

        this.$emit("update:modelValue", "");
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .input {
    width: 100%;
    outline: none;
    padding: 10px;
    border: 1px solid #b2b2b2;
    transition: 120ms all;

    &:focus {
      border-color: #000000;
    }
  }

  .btn {
    cursor: pointer;
    outline: none;
    width: 100px;
    border: none;
    background-color: #fec000;
    transition: 120ms all;

    &:hover {
      background-color: #efac02;
    }
  }
  </style>