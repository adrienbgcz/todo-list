<template>
  <div id="app">
    <layout>
      <template #header="slotProps">
      {{slotProps.appName}}
      </template>

      <template #main>
        <input-test @getTask="addTask" />

        <div v-for="(task, index) in tasksList" :key="`${task.taskName}${index}`" class="tasksList">
          <div :class="{ true: task.checked }">{{ task.taskName }}</div>
          <input type="checkbox" id="checkbox" v-model="task.checked" />
          <button-test @action="deleteTask(index)">Supprimer</button-test>
        </div>
      </template>

      <template #footer="slotProps">
      {{slotProps.mail}}
      </template>
    </layout>
  </div>
</template>

<script>
import InputTest from "./components/InputTest.vue";
import ButtonTest from "./components/ButtonTest.vue";
import Layout from "./components/Layout.vue";

export default {
  name: "App",
  components: {
    InputTest,
    ButtonTest,
    Layout,
  },
  data: function () {
    return {
      tasksList: [],
      checked: false,
    };
  },
  methods: {
    addTask(taskName) {
      let task = {
        taskName: taskName,
        checked: this.checked,
      };
      this.tasksList.push(task);
    },
    deleteTask(index) {
      this.tasksList.splice(index, 1);
    },
  },
};
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
