<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();

  let handleTodoFilter = filter => {
    dispatch("handleTodoFilter", {
      updatedFilter: filter
    });
  };

  export let currentFilter;
  export let activeTodos;
  export let showClearCompleted;
</script>

<style>
  .todo-footer {
    display: flex;
    align-items: center;
    width: calc(40% - 20px);
    color: #777;
    font-size: 14px;
    padding: 10px;
    height: 30px;
    background: #fff;
    border-bottom: 1px solid #e6e6e6;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2), 0 8px 0 -3px #f6f6f6,
      0 9px 1px -3px rgba(0, 0, 0, 0.2), 0 16px 0 -6px #f6f6f6,
      0 17px 35px -6px rgba(0, 0, 0, 0.2);
  }
  .todo-left-message {
    display: flex;
    width: 20%;
  }
  .todo-filter-container {
    display: flex;
    width: 59%;
    justify-content: space-evenly;
  }
  .todo-filter-container > div {
    cursor: pointer;
    padding: 3px 5px;
  }
  .todo-filter-container > div.active {
    border: 1px solid #8d8d8d;
  }
  .todo-clear-completed-msg {
    display: flex;
    width: 21%;
    cursor: pointer;
  }
  .todo-clear-completed-msg:hover {
    text-decoration: underline;
  }
</style>

<div class="todo-footer">
  <div class="todo-left-message">
    {activeTodos} items left
  </div>
  <div class="todo-filter-container">
    <div 
      on:click={() => handleTodoFilter("All")}
      class:active="{currentFilter === "All"}"
    >
      All
    </div>
    <div
      on:click={() => handleTodoFilter("Active")}
      class:active="{currentFilter === "Active"}"
    >
      Active
    </div>
    <div 
      on:click={() => handleTodoFilter("Completed")}
      class:active="{currentFilter === "Completed"}"
    >
      Completed
    </div>
  </div>
  {#if showClearCompleted}
      <div class="todo-clear-completed-msg">
        Clear Completed
      </div>
    {/if}
</div>