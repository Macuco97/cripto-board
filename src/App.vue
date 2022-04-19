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
      criptoValue: null,
      chosenDate: null, 
      history: null
    }
  },
 
  methods: {
    async getApiStatus(){
      const res = await fetch(`https://api.coingecko.com/api/v3/ping`)
      const data = await res.json()
      this.apiStatus = data.gecko_says === "(V3) To the Moon!"
    },

    async getCriptoValue(){
        const res = await fetch(`https://api.coingecko.com/api/v3/simple/price?ids=${this.chosenCripto}&vs_currencies=brl%2Cusd%2Ceur`)
        const data = await res.json()
        this.criptoValue = data
      
    },

    async getHistory(){
		if (this.chosenCripto != null) {
			const res = await fetch(`https://api.coingecko.com/api/v3/coins/${this.chosenCripto}/history?date=${this.chosenDate}&localization=false`)
       		const data = await res.json()
      		this.history = data
		}
		else {
			alert ("Choose some Cripto")
		}
		
    },

    setChosenCripto(value) {
      this.chosenCripto = value
    },

    setChosenDate(date){
      this.chosenDate = date
    }
  },

  watch: {
    chosenCripto: "getCriptoValue",
    chosenDate: 'getHistory'
  }

}
</script>


<template>
  <div class = 'bg-dark'>
    <div class="container py-5 vh-100">
      <Nav
      @setChosenCripto = "setChosenCripto"
      @date = "setChosenDate"
      />

      <div class="row">
      <div class=" text-white col-md-6 offset-md-3">
        <Card
        :criptoValue = criptoValue
        :chosenDate = chosenDate
        />
      </div>
      </div>  
    </div>
  </div>
</template>


