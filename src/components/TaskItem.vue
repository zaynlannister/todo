<template>
  <tr>
    <td>
      <span
          :class="{'finished': task.status === 'finished'}"
      >{{ task.title }}</span>
    </td>
    <td @click="this.$emit('change', task)" class="task__status">
      <span
          :class="getTodoClassNames"
      >{{ task.status }}</span>
    </td>
    <td>
      <div @click="this.$emit('edit', task)" class="task__icon">
        <span class="fa fa-pen"></span>
      </div>
    </td>
    <td>
      <div @click="this.$emit('delete', task)" class="task__icon">
        <span class="fa fa-trash"></span>
      </div>
    </td>
  </tr>
</template>

<script>
export default {
  props: {
    task: Object
  },

  computed: {
    getTodoClassNames() {
      const allowedClasses = {
        "to-do": "to-do",
        "in-progress": "in-progress",
        "finished": "finished-status",
      }

      return allowedClasses[this.task.status];
    }
  }
}
</script>

<style scoped lang="scss">
  .task {
    &__icon {
      width: fit-content;
      margin: 0 auto;
      cursor: pointer;
    }

    &__status {
      text-align: center;
      cursor: pointer;
      user-select: none;
    }
  }

  .finished {
    text-decoration: line-through;
  }

  .in-progress {
    color: #012cca;
  }

  .to-do {
    color: #d70606;
  }

  .finished-status {
    color: #069e67;
  }
</style>