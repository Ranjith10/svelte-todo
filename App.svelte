<script>
	import Todo from "./Todo.svelte";
</script>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
  }
  .todo-header {
    color: rgba(175, 47, 47, 0.45);
    font-weight: 600;
    font-size: 34px;
    text-align: center;
  }
</style>

<main>
	<h1 class="todo-header">Todo Manager</h1>
	<Todo />
</main>