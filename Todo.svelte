<script>
  let todo = "";
  let todoList = [];
  function handleTodoSubmit() {
    console.log(todo);
    todoList = [...todoList, todo];
    console.log(todoList);
    todo = "";
  }
</script>

<style>
</style>

<form on:submit|preventDefault={handleTodoSubmit}>
  <input 
    bind:value={todo}
    type="text"
    placeholder="What needs to be done?"
  />
</form>