<template>
    <div>
      <button @click="$emit('click')">
      <slot>Button</slot>

      </button>
        
    </div>
</template>


<script>
export default {
  name: 'ButtonTest',
  
  data: function () {
    return {
      
    }
  }
}
</script>
