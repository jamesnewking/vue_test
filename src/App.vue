<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/todo">Todo</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding:  0;
}

.btn {
  display: inline-block;
  border: none;
  background: lightgray;
  color: black;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
  color: white;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
