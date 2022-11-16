<template>
  <div class="todo">
    <h2 class="todo__header">My Vue Todo App</h2>
    <div class="todo__action">
      <input class="input default-border" type="text" placeholder="Enter task">
      <button class="btn">SUBMIT</button>
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
      <tr>
        <td>cook dinner</td>
        <td class="task__status">To-do</td>
        <td>
          <div class="task__icon">
            <span class="fa fa-pen"></span>
          </div>
        </td>
        <td>
          <div class="task__icon">
            <span class="fa fa-trash"></span>
          </div>
        </td>
      </tr>
      <tr>
        <td>learn js</td>
        <td class="task__status">To-do</td>
        <td>
          <div class="task__icon">
            <span class="fa fa-pen"></span>
          </div>
        </td>
        <td>
          <div class="task__icon">
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