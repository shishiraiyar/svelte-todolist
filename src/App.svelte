<script>
  import TodoList from './lib/TodoList.svelte';

  let taskList = JSON.parse(localStorage.getItem('taskList'))

  function clearAllTasks(){
    if(confirm("Are you sure you want to clear all tasks?")){
      taskList = []
      localStorage.clear()
    }

  }
</script>

<main>

  <h1>Todo List</h1>
    <TodoList taskList={taskList??[]}/>
    <button on:click={clearAllTasks}>Clear all Tasks</button>
  <p>Click on a task to mark it as done</p>

</main>

<style>

</style>
