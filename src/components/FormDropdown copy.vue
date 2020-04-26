<template>
  <div class="form-dropdown">
    <div class="asd"></div>
    <select @change="getChosenProduct">
      <option class="option" selected disabled>Options</option>
      <option
        v-for="(str, index) in optionsArray" :key="index"
        class="option"
      >{{str}}</option>
    </select>
  </div>
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
  position: relative
  height: 30px
  border-radius: 5px
  border: 1px solid black
  cursor: pointer
.asd
  width: 100%
  height: 30px
  position: absolute
  top: 0
  left: 0
  background-color: red
</style>
