<template>
  <div class="form-dropdown-holder">
    <select ref="select" @change="getChosenProduct" class="form-select">
      <option selected disabled>Options</option>
      <option v-for="(str, index) in optionsArray" :key="index">{{str}}</option>
    </select>

    <span class="form-dropdown-text">{{dropdownText}}</span>
    <span class="form-dropdown-arrow">&#9660;</span>
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
  data() {
    return {
      dropdownText: "Options"
    };
  },
  methods: {
    getChosenProduct() {
      const selectedText = this.$refs["select"].value;
      this.dropdownText = selectedText;
      return this.$emit("productName", selectedText);
    }
  }
};
</script>

<style scoped lang="sass">
.form-dropdown-holder
  position: relative
  height: 30px
  display: flex
  justify-content: space-between
  align-items: center
  border: 1px solid black
  border-radius: 5px
  text-align: left
  user-select: none
  white-space: nowrap
  cursor: pointer

.form-select
  opacity: 0
  position: absolute
  top: 0
  left: 0
  width: 100%
  height: 30px

$form-dropdown-arrow-width: 30px
.form-dropdown-text
  width: calc( 100% - #{$form-dropdown-arrow-width} - 15px )
  padding-left: 5px
  font-size: 12.5px
  overflow: hidden
.form-dropdown-arrow
  width: $form-dropdown-arrow-width
  height: 100%
  display: flex
  justify-content: center
  align-items: center
  border-radius: 0 5px 5px 0
  background-color: #E6E6E6
  border-bottom: 1px solid black
  border-top: 1px solid black
  border-left: 1px solid black
</style>
