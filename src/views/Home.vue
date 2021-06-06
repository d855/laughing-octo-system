<template>
    <img alt="Vue logo" src="../assets/logo.png">
</template>

<script>
import AgCookie from '../agCookie'
export default {
  data() {
    return {
      lang: null,
      cookies: null
    }
  }, 
  mounted(){
    this.cookies = new AgCookie;
    this.lang = this.cookies.read('language')
    if(this.lang == 'en'){
      this.$router.push('/lang/en');
    } else if (this.lang == 'rs'){
      this.$router.push('/lang/rs');
    }
  }
}
</script>

