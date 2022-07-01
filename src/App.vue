<template>
  <div id="app">
    <h2 class="header">Blog</h2>
    <nav>
      <router-link to="/" 
        style="display: inline-block;
        margin-right: 10px;
        font-weight: bold;
        color: #2c3e50;
        text-decoration: none;"
    >Home</router-link>
    
      <router-link to="/new-article" 
        style="display: inline-block;
        margin-right: 10px;
        font-weight: bold;
        color: #2c3e50;
        text-decoration: none;"
    >Dodaj nowy artykuł</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  width: 80vw;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  //  text-align: center;
  color: #2c3e50;
}
.header {
  margin: 20px 0;
}
nav {
  border-top: 2px solid black;
  border-bottom: 2px solid black;
  padding: 20px;
}
    a.router-link-exact-active {
      color: #42b983;
    }
</style>
