<script>
  import { createEventDispatcher } from "svelte";

  export let todoList;
  export let activeTodos;
  export let showClearComplete;
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
    justify-content: space-around;
  }
  .todo-filter-container > div {
    cursor: pointer;
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
    <div>All</div>
    <div>Active</div>
    <div>Completed</div>
  </div>
  {#if showClearComplete}
      <div class="todo-clear-completed-msg">
        Clear Completed
      </div>
    {/if}
</div>