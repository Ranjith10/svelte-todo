<script>
  import { createEventDispatcher } from "svelte";
</script>

<style>
  .todo-footer {
    display: flex;
    align-items: center;
    width: calc(40% - 20px);
    padding: 10px;
    height: 30px;
    background: #fff;
    border-bottom: 1px solid #e6e6e6;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
  }
  .todo-left-message {
    display: flex;
    width: 10%;
  }
  .todo-filter-container {
    display: flex;
    width: 90%;
  }
</style>

<div class="todo-footer">
  <div class="todo-left-message">
  </div>
  <div class="todo-filter-container">
    <div>All</div>
    <div>Active</div>
    <div>Completed</div>
    <div class="todo-clear-completed-msg">
      Clear Completed
    </div>
  </div>
</div>