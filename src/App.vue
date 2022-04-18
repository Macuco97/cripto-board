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
      }
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
      console.log(cripto != null, VS != null)
      if( cripto != null && VS != null ) {
        console.log(cripto, VS)
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
  <div v-if = 'apiStatus' class = 'container-fluid bg-dark text-white vh-100 px-0'> 
    <div class = 'row'></div>
      <Nav
      @setChosenCripto = 'setChosenCripto'
      @setChosenVS = 'setChosenVS'
      />
    </div>  
  <Error v-else/>
</template>

