<script>
import Error from './components/Error.vue'
import Nav from './components/Nav.vue'

export default {
  name: "App",
  components: {
    Error, Nav
  },
  data() {
    return {
      apiStatus: true,
      btcVsUsd: null,
    }
  },
  beforeMount(){
    this.getData()
    this.getbtcVsUsd()
    this.getCoinsList()
  },
  methods: {
    async getData(){
      const res = await fetch(`https://api.coingecko.com/api/v3/ping`)
      const data = await res.json()
      this.apiStatus = data.gecko_says === "(V3) To the Moon!"
    },

    async getbtcVsUsd(){
      const res = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=usd')
      const data = await res.json()
      const bitcoin = data.bitcoin
      const bitcoinVsUsb = bitcoin.usd
      this.btcVsUsd = bitcoinVsUsb
    },

};
</script>


<template>
  <div v-if = 'apiStatus' class = 'container-fluid bg-dark text-white vh-100 px-0'> 
    <div class = 'row'></div>
      <Nav/>
    </div>  
  <Error v-else/>
</template>

