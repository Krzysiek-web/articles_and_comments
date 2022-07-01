<template>
  <div class="article">
    <ArticleComponent :id="id" />
    <CustomDialogComponent :id="id"/>
   </div>
</template>

<script>
import ArticleComponent from "@/components/ArticleComponent.vue";
import CustomDialogComponent from '@/components/CustomDialogComponent.vue';

export default {
    
  name: "ArticleView",
  components: {
    ArticleComponent,
    CustomDialogComponent,
    
},
  props: {
    id: {
      type: [Number, String],
      required: true,
    },
  },
 
  
};
</script>
