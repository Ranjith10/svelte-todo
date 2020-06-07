<script>
  import TodoItem from "./TodoItem.svelte";
  import TodoFooter from "./TodoFooter.svelte";

  let todo = "";
  let todoList = [];
  let id = 0;
  let currentFilter = "All";

  let handleTodoAction = event => {
    let action = event.detail ? event.detail.action : event.action;
    switch (action) {
      case "add-todo": {
        if (todo.trim().length > 0) {
          let todoItem = {
            id: id++,
            todoItem: todo,
            completed: false
          };
          todoList = [todoItem, ...todoList];
          return todoList;
        }
        return;
      }
      case "delete-todo": {
      }
      case "toggle-completed-status": {
        let todos = todoList;
        let id = event.detail.id;
        todos.forEach(todo => {
          if (todo.id === id) {
            todo.completed = !todo.completed;
          }
        });
        todoList = todos;
        return todoList;
      }
      case "clear-completed-todo": {
      }
      default: {
        return todoList;
      }
    }
  };

  let handleTodoSubmit = () => {
    handleTodoAction({
      action: "add-todo"
    });
    todo = "";
  };

  let handleTodoFilter = event => {
    currentFilter = event.detail.updatedFilter;
  };

  $: activeTodos = todoList.filter(todo => !todo.completed).length;
  $: showClearCompleted = todoList.filter(todo => todo.completed).length > 0;

  $: filteredTodos =
    currentFilter === "All"
      ? todoList
      : currentFilter === "Active"
      ? todoList.filter(todo => !todo.completed)
      : todoList.filter(todo => todo.completed);
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
    {#each filteredTodos as todo, index}
      <TodoItem 
        {...todo}
        on:toggle = {handleTodoAction}
      />
    {/each}
  </div>
  {#if todoList.length > 0}
    <TodoFooter 
      {activeTodos}
      {showClearCompleted}
      {currentFilter}
      on:handleTodoFilter={handleTodoFilter}
    />
  {/if}
  
</div>
