<template>
  <div class="todo">
    <h2 class="todo__header">My Vue Todo App</h2>
    <div class="todo__action">
      <input class="default-border" type="text" placeholder="Enter task">
      <button>SUBMIT</button>
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
        <td>icon</td>
        <td>icon</td>
      </tr>
      <tr>
        <td>learn js</td>
        <td class="task__status">To-do</td>
        <td>icon</td>
        <td>icon</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {

}
</script>

<style>
  input {
    width: 100%;
    outline: none;
    padding: 10px;
    border: 1px solid #b2b2b2;
  }

  button {
    cursor: pointer;
    outline: none;
    width: 100px;
    border: none;
    background-color: #fec000;
  }

  .todo {
    width: 800px;
    margin: 0 auto;
  }

  .todo__header {
    text-align: center;
    font-weight: 500;
  }

  .todo__action {
    display: flex;
    margin: 10px 0 40px;
  }

  table, th, td {
    border: 1px solid #b2b2b2;
    border-collapse: collapse;
    padding: 6px;
  }

  .table {
    width: 100%;
  }

  .todo__task {
    width: 60%;
    text-align: left;
  }

  .todo__status {
    width: 30%;
  }

  .task__status {
    text-align: center;
    cursor: pointer;
  }

  .todo__icon {
    width: 5%;
  }
</style>