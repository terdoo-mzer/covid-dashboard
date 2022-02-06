<template>
  
    <Header />
    <Home />
  
</template>

<script>
import Home from '@/components/Home.vue'
import Header from '@/components/Header.vue'


export default {
  name: 'App',
  components: {
    Home,
    Header
  },
  data() {
    return {
      loading: false
    }
  }
}
</script>

