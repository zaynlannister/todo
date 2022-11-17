<template>
  <div class="todo">
    <h2 class="todo__header">My Vue Todo App</h2>
    <div class="todo__action">
      <input v-model="inputValue" class="input default-border" type="text" placeholder="Enter task">
      <button @click="addTask" class="btn">SUBMIT</button>
    </div>

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
      <tr v-for="task in tasks">
        <td>{{ task.title }}</td>
        <td class="task__status">{{ task.status }}</td>
        <td>
          <div @click="editTask(task)" class="task__icon">
            <span class="fa fa-pen"></span>
          </div>
        </td>
        <td>
          <div @click="deleteTask(task)" class="task__icon">
            <span class="fa fa-trash"></span>
          </div>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: '',
      editedTask: null,
      tasks: [
        {id: 1, title: "cook dinner", status: "to-do"},
        {id: 2, title: "learn js", status: "to-do"}
      ]
    }
  },

  methods: {
    addTask() {
      if (this.inputValue.length === 0) return;

      if (this.editedTask === null) {
        this.tasks.push({
          id: Date.now(),
          status: "to-do",
          title: this.inputValue
        })
        this.inputValue = "";
      } else {
        this.editedTask.title = this.inputValue;
        this.inputValue = "";
        this.editedTask = null;
      }
    },

    deleteTask(task) {
      this.tasks = this.tasks.filter(item => item.id !== task.id);
    },

    editTask(task) {
      this.inputValue = task.title;
      this.editedTask = task;
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
    }
  }
</style>