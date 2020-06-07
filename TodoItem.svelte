<script>
  import { createEventDispatcher } from "svelte";

  export let todoItem;
  export let id;
  export let completed;

  const dispatch = createEventDispatcher();

  function dispatchToggleTodo() {
    dispatch("toggle", {
      action: "toggle-completed-status",
      id: id
    });
  }
</script>

<style>
  .todo-item-container {
    display: flex;
    padding: 5px;
    border-bottom: 1px solid #ededed;
  }
  .todo-item {
    display: flex;
    height: 50px;
    justify-content: flex-start;
    align-items: center;
    width: calc(100% - 60px);
  }
  .todo-done-toggle {
    position: relative;
    width: 50px;
  }
  .todo-done-toggle input[type="checkbox"] {
    visibility: hidden;
  }
  .todo-done-toggle input[type="checkbox"]:checked + label {
    background-color: #fff;
    border-color: #66bb6a;
  }
  .todo-done-toggle label {
    border-radius: 50%;
    background-color: #fff;
    border: 1px solid #ccc;
    cursor: pointer;
    height: 30px;
    width: 30px;
    position: absolute;
    top: 10px;
    left: 10px;
  }
  .todo-done-toggle input[type="checkbox"]:checked + label:after {
    opacity: 1;
  }
  .todo-done-toggle label:after {
    border: 2px solid #66bb6a;
    border-top: none;
    border-right: none;
    content: "";
    height: 6px;
    left: 7px;
    opacity: 0;
    position: absolute;
    top: 8px;
    transform: rotate(-45deg);
    width: 12px;
  }
  .todo-item.complete {
    color: #8d8d8d;
    text-decoration: line-through;
  }
</style>

<div class="todo-item-container">
  <div class="todo-done-toggle">
    <input 
      type=checkbox
      id={`checkbox${id}`}
      bind:checked={completed}
    >
    <label 
      on:click={dispatchToggleTodo}
      htmlFor = {`checkbox${id}`}
    />
  </div>
  <div 
    key={id}
    class="{completed ? 'todo-item complete' : 'todo-item'}" 
  >
    {todoItem}
  </div>
</div>