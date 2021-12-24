<template>
  <div class="inputTest">
    <input type="text" v-model="inputValue" @keyup.enter="getTask" @click="cleanInput">
    <button-test @click="getTask">Valider</button-test>
  </div>
</template>

<script>
import ButtonTest from "./ButtonTest.vue"

export default {
  name: 'InputTest',
  components: {
    ButtonTest
  },
  
  data: function () {
    return {
      inputValue: ''
    }
  },
  methods: {
    getTask() {
      this.$emit('getTask', this.inputValue);
    },
    cleanInput() {
      this.inputValue = '';
    }
  }
}
</script>

<style scoped>
 .inputTest {
   display: flex;
   margin-bottom: 50px;
   margin-right: 20px;
 }

</style>
