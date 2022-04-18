<script>
import Error from './components/Error.vue'
import Nav from './components/Nav.vue'
import Card from './components/Card.vue'



export default {
  name: "App",
  components: {
    Error, Nav, Card
  },
  
   beforeMount(){
    this.getApiStatus()
  },

  data() {
    return {
      apiStatus: true,
      chosenCripto: null,
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
        const res = await fetch(`https://api.coingecko.com/api/v3/simple/price?ids=${this.chosenCripto}&vs_currencies=brl%2Cusd%2Ceur`)
        const data = await res.json()
        this.criptoValue = data
      
    },

    setChosenCripto(value) {
      this.chosenCripto = value
    },
  },

  watch: {
    chosenCripto: "getCriptoValue"
  }

}
</script>


<template>
  <div class = 'bg-dark'>
    <div class="container py-5 vh-100">
      <Nav
      @setChosenCripto = "setChosenCripto"
      />

      <div class="row">
      <div class=" text-white col-md-6 offset-md-3">
        <Card
        :criptoValue = criptoValue
        />
      </div>
      </div>  
    </div>
  </div>
</template>


