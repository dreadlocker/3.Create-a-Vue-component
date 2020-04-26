<template>
  <button @click.prevent="submit" class="btn-submit" type="submit">{{text}}</button>
</template>

<script>
export default {
  name: "FormButton",
  props: {
    allProductsObj: {
      type: Object,
      required: true
    },
    text: {
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
      const generatingLinksArray = [];
      filteredProductsArray.forEach(obj => generatingLinksArray.push({
        store: obj.store,
        cb_id: obj.cb_id,
        currency: obj.currency,
      }));
      
      return this.$emit("generatingLinksArray", generatingLinksArray);

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
