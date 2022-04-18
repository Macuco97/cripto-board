<script>
import { watch } from '@vue/runtime-core';
import Error from './components/Error.vue'
import Nav from './components/Nav.vue'

export default {
  name: "App",
  components: {
    Error, Nav
  },
  
   beforeMount(){
    this.getApiStatus()
  },

  data() {
    return {
      apiStatus: true,
      btcVsUsd: null
    }
  },
 
  methods: {
    async getApiStatus(){
      const res = await fetch(`https://api.coingecko.com/api/v3/ping`)
      const data = await res.json()
      this.apiStatus = data.gecko_says === "(V3) To the Moon!"
    }
  }

};
</script>


<template>
  <div v-if = 'apiStatus' class = 'container-fluid bg-dark text-white vh-100 px-0'> 
    <div class = 'row'></div>
      <Nav/>
    </div>  
  <Error v-else/>
</template>

