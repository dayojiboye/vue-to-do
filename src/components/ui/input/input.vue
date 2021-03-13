<template>
  <input
    v-bind="attr"
    :value="value"
    @input="handleInput($event.target.value)"
  />
</template>

<script>
export default {
  props: ["value", "attr"],
  data() {
    return {
      content: this.value
    };
  },
  methods: {
    handleInput(value) {
      this.$emit("input", value);
    }
  }
};
</script>
