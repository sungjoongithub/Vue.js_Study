<template>
<div id="app">
  <Header></Header>
    <Body></Body>
    <Left></Left>
    <Footer></Footer>
</div>
</template>

<script>
import Header from './components/Header.vue'
import Body from './components/Body.vue'
import Left from './components/Left.vue'
import Footer from './components/Footer.vue'
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
 
components: {
    'Header': Header,
    'Body': Body,
    'Left': Left,
    'Footer': Footer
  }
}

  
</script>

<style>
</style>
