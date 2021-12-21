<template>
  <div class="inputTest">
    <input type="text" v-model="inputValue" >
    <button-test label="Valider" @action="getTask()"/>
  </div>
</template>

<script>
import ButtonTest from "./buttonTest.vue"

export default {
  name: 'inputTest',
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
      this.$emit('getTask', this.inputValue)
    }
  }
}
</script>

<style scoped>
 .inputTest {
   display: flex;
 }

</style>
