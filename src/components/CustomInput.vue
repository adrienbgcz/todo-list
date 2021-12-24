<template>
  <div>
    <div>{{ label }}</div>
    <input :value="value" @input="$emit('input', $event.target.value)" >
  </div>
</template>

<script>
export default {
  name: "CustomInput",
  props: {
    label: {
      type: String,
      required: true,
    },
    value: {
        type: String,
        required: false
    }
  },
  data: function () {
    return {
      inputValue: ""
    };
  },
};
</script>
