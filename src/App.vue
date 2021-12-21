<template>
  <div id="app">
    <input-test @getTask="addTask" />

    <div v-for="(task, index) in tasksList" :key="task.taskName" class="tasksList" >
      <div :class="{true:task.checked}">{{task.taskName}}</div>
      <input type="checkbox" id="checkbox" v-model="task.checked" >
      <button-test label="Supprimer" @action="deleteTask(index)"/>
    </div>
    
  </div>
</template>

<script>
import InputTest from "./components/inputTest.vue"
import ButtonTest from "./components/buttonTest.vue"

export default {
  name: 'App',
  components: {
    InputTest,
    ButtonTest
  }, 
  data: function() {
    return {
      tasksList: [], 
      checked: false
    }
  },
  methods: {
    addTask(taskName) {
      let task = {
        taskName: taskName,
        checked: this.checked
      }
      this.tasksList.push(task)
    },
    deleteTask(index) {
      this.tasksList.splice(index, 1)
    }
  }
}
</script>

<style>

.tasksList {
  display: flex;
}

.true {
  color: red;
  text-decoration: line-through;
}

</style>
