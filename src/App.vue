<template>
  <div id="app">
    <header>
      <div class="content">
        <router-link tag="h1" :to="{name: 'Products'}">
          <a>JS' Dairy Farm</a>
        </router-link>
      </div>
    </header>
    <router-view class="content main"/>
    <footer>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
html, body, #app {
  margin: 0;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  display: flex;
  flex-direction: column;
}

header, footer {
  background-color: #61bdff;
  width: 100%;
  padding: 1em 0;
  flex:0 0 auto;
}

.content {
  width: 38em;
  max-width: 100%;
  margin: auto;
  box-sizing: border-box;
  padding: 0 1em;
}

.main {
  flex:1 1 100%;
  padding: 3em 1em;
}

h1 a:before {
  display: inline-block;
  content: "";
  width: 1.5em;
  height: 1.5em;

  position: relative;
  top: .25em;

  background-image: url('/static/logo.svg');
  background-repeat: no-repeat;
}

h1 a {
  color: inherit;
  text-decoration: none;
}
</style>
