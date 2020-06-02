<script>
  import TodoItem from "./TodoItem.svelte";
  let todo = "";
  let todoList = [];
  let id = 0;
  const handleTodoSubmit = () => {
    dispatchTodo({
      type: "add-todo",
      todo: todo
    });
    todo = "";
  };
  const dispatchTodo = action => {
    switch (action.type) {
      case "add-todo": {
        let todoItem = {
          id: id++,
          todoItem: todo,
          active: true
        };
        todoList = [todoItem, ...todoList];
        return todoList;
      }
      case "toggle-todo": {
        console.log("called");
        todoList.forEach(todo => {
          if (todo.id === action.id) {
            todo.active = !todo.active;
          }
        });
        return todoList;
      }
      default: {
        return todoList;
      }
    }
  };
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
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .todo-input-container > form {
    width: 40%;
  }
  .todo-list-container {
    display: flex;
    flex-direction: column;
    width: 40%;
    background: white;
    border-top: 1px solid #e6e6e6;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
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
  
  <div class="todo-list-container">
    {#each todoList as todo, index}
      <TodoItem 
        {...todo}
        on:dispatch = {dispatchTodo}
      />
    {/each}
  </div>
</div>
