<template>
  <form action="" method="get" class="form">
    <div class="form-left-side">
      <FormDropdown
        :optionsArray="optionsArray"
        @productName="saveProductName"
      />
      <FormButton
        :allProductsObj="allProductsObj"
        :text="text"
        :productName="productName"
        @generatingLinksArray="sendArrayToFormOutput"
      />
    </div>

    <div class="form-right-side">
      <FormOutput
        :generatingLinksArray="generatingLinksArray"
      />
    </div>
  </form>
</template>

<script>
import FormDropdown from "./FormDropdown.vue";
import FormButton from "./FormButton.vue";
import FormOutput from "./FormOutput.vue";
import api from "@/assets/api.json";
// import axios from "axios";

/**
 * I can't make a GET request from localhost - error:
 * Access to XMLHttpRequest at 
 * 'https://www.acronis.com/en-us/api/v1/price/?machine_name=acronis_backup&locale=en-us' 
 * from origin 'http://localhost:8080' has been blocked by CORS policy: 
 * No 'Access-Control-Allow-Origin' header is present on the requested resource.
 * 
 * so I'm using local JSON file, so I can complete the task
 */


export default {
  name: "MainForm",
  components: {
    FormDropdown,
    FormButton,
    FormOutput,
  },
  data() {
    return {
      allProductsObj: [],
      optionsArray: [],
      text: "Search",
      productName: "",
      generatingLinksArray: []
    };
  },
  methods: {
    saveProductName(str) {
      return this.productName = str;
    },
    sendArrayToFormOutput(arr) {
      return this.generatingLinksArray = arr;
    }
  },
  beforeMount() {
    // const url = "https://www.acronis.com/en-us/api/v1/price/?machine_name=acronis_backup&locale=en-us";
    // axios(url, {
    //   method: "GET",
    //   mode: "no-cors",
    //   headers: {
    //     "Access-Control-Allow-Origin": "*",
    //     "Content-Type": "application/json",
    //   },
    //   withCredentials: true,
    //   credentials: "same-origin",
    // }).then(response => {
    //   console.log(response);
    // });

    this.allProductsObj = api.subscription.buy;
    const optionsArray = [];
    for (const key in this.allProductsObj) {
      const obj = this.allProductsObj[key];
      optionsArray.push(obj.product_name);
    }
    return this.optionsArray = optionsArray;

    // const url = "https://www.acronis.com/en-us/api/v1/price/?machine_name=acronis_backup&locale=en-us";
    // axios.get(url)
    //   .then(function (response) {
    //     console.log(response);
    //   })
    //   .catch(function (error) {
    //     console.log(error);
    //   });
  }
};
</script>

<style scoped lang="sass">
$form-left-side-width: 150px
$form-left-side-margin-right: 30px
$form-right-side-width: 320px
  
.form
  display: flex
  justify-content: space-between
  align-items: flex-start
  width: calc( #{$form-left-side-width} + #{$form-left-side-margin-right} + #{$form-right-side-width} )
  margin: auto
.form-left-side
  width: $form-left-side-width
  display: flex
  flex-direction: column
  margin-right: $form-left-side-margin-right
.form-right-side
  width: $form-right-side-width
</style>
