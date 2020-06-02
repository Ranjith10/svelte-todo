<script>
  let todo = "";
  let todoList = [];
  function handleTodoSubmit() {
    todoList = [...todoList, todo];
    todo = "";
  }
</script>

<style>
  .todo-input {
    margin: 30px 0px 0;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
    background: #ffffff;
    width: calc(100% - 60px);
    min-height: 50px;
    border: none;
    padding: 10px 10px 10px 50px;
    font-size: 22px;
  }
  .todo-input-container {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .todo-input-container > form {
    width: 550px;
  }
</style>

<div class="todo-input-container">
  <form on:submit|preventDefault={handleTodoSubmit}>
    <input 
      class="todo-input"
      bind:value={todo}
      type="text"
      placeholder="What needs to be done?"
    />
  </form>
</div>