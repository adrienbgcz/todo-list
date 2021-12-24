<template>
  <div id="app">
    <layout>
      <template #header="{appName}"> <!-- EX destructuring des slots props -->
      {{appName}}
      </template>

    
        <input-test @getTask="addTask" />

        <div v-for="(task, index) in tasksList" :key="`${task.taskName}${index}`" class="tasksList">
          <div :class="{ true: task.checked }">{{ task.taskName }}</div>
          <input type="checkbox" id="checkbox" v-model="task.checked" />
          <button-test @click="deleteTask(index)">Supprimer</button-test>
        </div>
    

      <template #footer="slotProps"> <!-- EX slots props classiques-->
      {{slotProps.mail}}
      </template>
    </layout>

    <custom-input label="test"  v-model="inputValue" /> 
    <!-- v-model exclusivement lié à l'évènement input-->
    <!-- v-model = "inputValue"   ===> :value="inputValue" @input="inputValue=$event"-->
    
  </div>
</template>

<script>
import InputTest from "./components/InputTest.vue";
import ButtonTest from "./components/ButtonTest.vue";
import Layout from "./components/Layout.vue";
import CustomInput from "./components/CustomInput.vue";

export default {
  name: "App",
  components: {
    InputTest,
    ButtonTest,
    Layout,
    CustomInput
  },

  data: function () {
    return {
      tasksList: [],
      checked: false,
      inputValue: "kgvljbk"
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
    getInputValue(value) {
      this.inputValue = value         //à supprimer
      console.log(this.inputValue)
    }
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
