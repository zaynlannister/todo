<template>
  <table class="table">
    <thead>
    <tr>
      <th class="todo__task">Task</th>
      <th class="todo__status">Status</th>
      <th class="todo__icon">#</th>
      <th class="todo__icon">#</th>
    </tr>
    </thead>
    <tbody>

    <task-item
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @delete="this.$emit('delete', task)"
      @edit="this.$emit('edit', task)"
      @change="this.$emit('change', task)"
    />

    </tbody>
  </table>
</template>

<script>
import TaskItem from "@/Components/TaskItem.vue";

export default {
  components: {
    TaskItem,
  },

  props: {
    tasks: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>