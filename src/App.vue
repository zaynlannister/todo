<template>
  <div class="todo">
    <h2 class="todo__header">My Vue Todo App</h2>

    <post-form
      @create="addTask"
      v-model="inputValue"
    />

    <task-table
      :tasks="tasks"
      @delete="deleteTask"
      @edit="editTask"
      @change="changeStatus"
    />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import TaskTable from "@/components/TaskTable.vue";

export default {
  components: {
    PostForm,
    TaskTable
  },

  data() {
    return {
      inputValue: "",
      editedTask: null,
      availableStatuses: ["to-do", "in-progress", "finished"],
      tasks: []
    }
  },

  methods: {
    addTask(task) {
      if (this.editedTask) {
        const taskIndex = this.tasks.findIndex(item => item.id === this.editedTask.id);
        this.tasks[taskIndex] = task;

        this.editedTask = null;
      } else {
        this.tasks.push(task);
      }
    },

    deleteTask(task) {
      this.tasks = this.tasks.filter(item => item.id !== task.id);
    },

    editTask(task) {
      this.inputValue = task.title;
      this.editedTask = task;
    },

    changeStatus(task) {
      let newIndex = this.availableStatuses.indexOf(task.status);

      if (++newIndex > 2) {
        newIndex = 0;
      }

      task.status = this.availableStatuses[newIndex];
    }
  }
}
</script>

<style lang="scss">
  .todo {
    width: 800px;
    margin: 0 auto;

    &__header {
      text-align: center;
      font-weight: 500;
    }

    &__action {
      display: flex;
      margin: 10px 0 40px;
    }

    &__task {
      width: 60%;
      text-align: left;
    }

    &__status {
      width: 30%;
    }

    &__icon {
      width: 5%;
    }
  }

  table, th, td {
    border: 1px solid #b2b2b2;
    border-collapse: collapse;
    padding: 6px;
  }

  .table {
    width: 100%;
  }
</style>