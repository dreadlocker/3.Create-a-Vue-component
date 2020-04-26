<template>
  <button @click.prevent="submit" class="btn-submit" type="submit">{{btnText}}</button>
</template>

<script>
export default {
  name: "FormButton",
  props: {
    allProductsObj: {
      type: Object,
      required: true
    },
    btnText: {
      type: String,
      required: true
    },
    productName: {
      type: String,
      required: true
    },
  },
  methods: {
    submit() {
      if(!this.productName) return;

      const allProductsArray = Object.values(this.allProductsObj);
      const filteredProductsArray = allProductsArray.filter(obj => obj.product_name === this.productName);
      const linksArray = filteredProductsArray.map(obj => `https://store.acronis.com/${obj.store}/purl-consumer-standard-US?cart=${obj.cb_id}&currencies=${obj.currency}`);
      
      return this.$emit("linksArray", linksArray);

    }
  }
};
</script>

<style scoped lang="sass">
.btn-submit
  width: 75px
  height: 30px
  border-radius: 5px
  cursor: pointer
  border: 1px solid black
  margin-top: 20px
  background-color: #E6E6E6
</style>
