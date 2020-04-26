<template>
  <select @change="getChosenProduct" class="form-dropdown">
    <option class="option" selected disabled>Options</option>
    <option
      v-for="(str, index) in optionsArray" :key="index"
      class="option"
    >{{str}}</option>
  </select>
</template>

<script>
export default {
  name: "FormDropdown",
  props: {
    optionsArray: {
      type: Array,
      required: true
    }
  },
  methods: {
    getChosenProduct() {
      return this.$emit("productName", this.$el.value);
    }
  }
};
</script>

<style scoped lang="sass">
.form-dropdown
  height: 30px
  border-radius: 5px
  border: 1px solid black
  cursor: pointer
</style>
