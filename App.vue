<template>
  <header>
    <router-link to="/">
      <h3>\V/ue<span> #Movie</span> Database</h3> 
    </router-link>
  </header>
  <main>
   <router-view/>
  </main>
</template>

<style lang="scss">
* {
  margin: 0; 
  padding: 0; 
  box-sizing: border-box;
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif; 

  &::selection { 
    background: transparentize(#222, 0.6);
  }
}

body { 
  background-color: #222; 
}

header { 
  display: flex; 
  align-items: center; 
  justify-content: center;
  padding: 12px 14px;
  background-color: #2d3e50;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

a { 
  text-decoration: none;
  
}

h3 {
  color: ghostwhite; 
  font-size: 1.35em;
}

p { 
  color: ghostwhite;
}

span { 
  color: #42b983;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
