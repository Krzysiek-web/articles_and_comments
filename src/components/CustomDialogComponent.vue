<template>
  <div>
    <md-dialog :md-active.sync="showDialog" :md-click-outside-to-close="false">
      <md-dialog-title>Dodaj komentarz</md-dialog-title>
      

      <TextFieldComponent @cancel="cancel($event)" :id="id"/>

    
    </md-dialog>
    <div class="button">
    <md-button class="md-primary md-raised" @click="showDialog = true">Dodaj komentarz</md-button>
    </div>
  </div>
</template>

<script>
 
import Vue from 'vue'
import { MdButton, MdDialog, } from 'vue-material/dist/components'
import 'vue-material/dist/vue-material.min.css'
import 'vue-material/dist/theme/default.css'
import TextFieldComponent from './TextFieldComponent.vue'


Vue.use(MdButton)
Vue.use(MdDialog)
 
  export default {
    props: {
    id: {
      type: [Number, String],
      required: true,
    },
  },
    name: "DialogCustom",
   
    data: () => ({
        showDialog: false,
       
        
    }),
    components: { TextFieldComponent,  },
    methods:{
      cancel(e){
        
        this.showDialog = e
      }

    }

}
</script>

<style lang="scss" scoped>
.button{
    display: flex;
    flex-direction: row;
    justify-content: end;
}
.md-dialog .md-dialog-container {
   width: 1024px;
   height: 1024px;
  }
</style>
