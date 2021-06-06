<template>
  <div id="nav">
    <router-link @click="changeCookieLang('en')" to="/lang/en">English</router-link> |
    <router-link @click="changeCookieLang('rs')" to="/lang/rs">Srpski</router-link>
  </div>
  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
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

<script>
  import AgCookie from './agCookie.js';
  export default {
    data(){
      return {
        cookieLang: ''
      }
    },
    methods: {
      changeCookieLang: function(lang) {
        this.cookieLang = lang;
        this.setCookie();
      },
      setCookie: function (){
        this.cookies = new AgCookie;
        this.cookies.create('language', this.cookieLang, 1)
      }
    }
  }
</script>