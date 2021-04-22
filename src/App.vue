<template>
  <div id="app">
    <Header titulo="TP5" autor="Carlitos Tevez"/>
    <Body/>
    <Footer titulo="TP5" autor="Carlitos Tevez"/>
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Body from "./components/Body.vue";
  import Footer from "./components/Footer.vue";

  export default {
    name: 'App',
    components: {
      Header,
      Body,
      Footer
    }
  }
</script>

<style>
</style>
