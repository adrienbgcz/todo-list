<template>
    <div>
      <button @click="$emit('action')">{{label}}</button>
        
    </div>
</template>


<script>
export default {
  name: 'buttonTest',
  props: {
    label: {
      type: String
    }
  },
  data: function () {
    return {
      buttonLabel: this.label
    }
  }
}
</script>
