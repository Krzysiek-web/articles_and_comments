<template>
  <div class="home">
    <ArticlesComponent />
  </div>
</template>

<script>
// @ is an alias to /src

import ArticlesComponent from "@/components/ArticlesComponent.vue";
export default {
  name: "HomeView",
  components: {
    ArticlesComponent,
  },
};
</script>
