<template>
  <Header></Header>
  <Message class="message"></Message>
  <LatestNews></LatestNews> 
  <Footer></Footer>
</template>

<script>
import Header from '../components/Header.vue'
import LatestNews from '../components/LatestNews.vue'
import Footer from '../components/Footer.vue'
import Message from '../components/Messages.vue'

export default {
  name: 'Message-page',
  components: {
    Header,
    Message,
    LatestNews,
    Footer
  }
}
</script>

<style scoped>
.emergency {
  height: 250px;
  display: block;
  margin-bottom: -20px;
}

.message {
  margin-bottom: 50px;
}
</style>