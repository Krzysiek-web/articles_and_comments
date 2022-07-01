<template>
  
    <md-button class="md-primary md-raised " @click="sendEvent">{{btnText}}</md-button>
    
  
</template>

<script>

import Vue from "vue";
import { MdButton } from "vue-material/dist/components";
import "vue-material/dist/vue-material.min.css";

Vue.use(MdButton);

export default {
  name: "DialogCustom",
 
   
  
  props: {
    btnText: {
      type: String,
      required: true,
      default: "custom button",
    }
  }
  
  
};
</script>

<style>

</style>