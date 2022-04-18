<script>
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
      chosen: {
        cripto: null, 
        VS: null
      },
      criptoValue: null

    }
  },
 
  methods: {
    async getApiStatus(){
      const res = await fetch(`https://api.coingecko.com/api/v3/ping`)
      const data = await res.json()
      this.apiStatus = data.gecko_says === "(V3) To the Moon!"
    },

    async getCriptoValue() {
      const { cripto, VS } = this.chosen
      if( cripto != null && VS != null ) {
        const res = await fetch(`https://api.coingecko.com/api/v3/simple/price?ids=${cripto}&vs_currencies=${VS}`)
        const data = await res.json()
        this.criptoValue = data[cripto][VS]
      }
    },

    setChosenCripto(value) {
      this.chosen.cripto = value
    },

    setChosenVS(value) {
      this.chosen.VS = value
    }
  },

  watch: {
    chosen: {
      handler() {
        this.getCriptoValue()
      },
      deep: true
    }
  }

}
</script>


<template>
  <div class = 'bg-dark'>
    <div class="container vh-100">
      <Nav/>
    </div>
  </div>
  
  
</template>


