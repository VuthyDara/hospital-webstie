<template>
  <Header></Header>
  <PatientTwo></PatientTwo>
  <LatestNews class="latest"></LatestNews> 
  <Footer></Footer>
</template>

<script>
import Header from '../components/Header.vue'
import LatestNews from '../components/LatestNews.vue'
import Footer from '../components/Footer.vue'
import Emergency from '../components/Emergency.vue'
import PatientTwo from '../components/PatientTwo.vue'

export default {
  name: 'Patient2',
  components: {
    Header,
    Emergency,
    PatientTwo,
    LatestNews,
    Footer,
  }
}
</script>

<style scoped>
.latest {
  margin-top:4em;
}
</style>