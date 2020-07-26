<template>
  <div id="app">
    <Header/>
    <ListCountries/>
    <Footer />
  </div>

</template>

<script>
import Header from './components/Header';
import ListCountries from './components/ListCountries';
import Footer from './components/Footerpage'

export default {
  name: 'App',
  components: {
    Header,
    ListCountries,
    Footer
  }
}
</script>

<style scoped>
    #app{
        background-color: whitesmoke;
    }
</style>>