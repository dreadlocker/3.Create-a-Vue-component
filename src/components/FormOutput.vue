<template>
  <div class="form-output">
    <div
      v-for="(link, index) in linksArray"
      :key="index"
      :class="{'link-holder': index < linksArray.length - 1}"
    >
      <a :href="link" target="_blank">{{link}}<br></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormOutput",
  props: {
    linksArray: {
      type: Array,
      required: true
    },
  }
};
</script>

<style scoped lang="sass">
.form-output
  border: 1px solid black
  padding: 15px
  text-align: left
.link-holder
  padding-bottom: 20px
</style>
