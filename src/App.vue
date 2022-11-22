<template>
  <div class="todo">
    <h2 class="todo__header">My Vue Todo App</h2>

    <post-form
      @create="addTask"
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
      tasks: [
        {id: 1, title: "cook dinner", status: "to-do"},
        {id: 2, title: "learn js", status: "to-do"}
      ]
    }
  },

  methods: {
    addTask(task) {
      if (this.editedTask === null) {
        this.tasks.push(task);
      } else {
        this.editedTask.title = this.inputValue;
        this.editedTask = null;
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
      console.log(task)
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