<template>
  <div id="app">

    <header>
      Minhas tarefas
    </header>
    <Task class="task" />

  </div>
</template>

<script>
import Task from './components/Task'
export default {
  name: 'App',
  components: {
    Task
  }
}
</script>

<style>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 80%;
  font-size: 40px;
  color: white;
}
</style>
