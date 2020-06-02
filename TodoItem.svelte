<script>
  export let todoItem;
  export let id;
  export let active;
</script>

<style>
  .todo-item {
    display: flex;
    height: 50px;
    justify-content: flex-start;
    align-items: center;
    border-bottom: 1px solid #ededed;
  }
</style>


<div 
  key={id}
  class="todo-item" 
>
  {todoItem}
</div>