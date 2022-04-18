<script>
	export default {
		name: "Card",
		props: {
        	      criptoValue: Object,
                  default: null
        	},
		data(){
                  return {
                        coin: "Choose your coin in SideMenu",
                        BRL: null, 
                        USD: null,
                        EUR: null
                  }
                  
		},
            methods: {
                  getValuesFromProps(){
                        const objectKey = (Object.keys(this.criptoValue)[0])
                        const coinsVs = this.criptoValue[objectKey]
                        this.coin = objectKey
                        this.BRL = coinsVs.brl
                        this.USD = coinsVs.usd
                        this.EUR = coinsVs.eur
                  }
            },
            watch: {
                  criptoValue: {
                        deep: true, 
                        handler: "getValuesFromProps"
                  }
            }
    	}	
</script>
<template>
      <div class="card bg-secondary" style = "width: 18rem;">
            <div class="card-header text-uppercase">{{ coin }}</div>
            <div class="card-body">
                  <h5 class="text-uppercase card-title">Price Currenty </h5>
                  <ul class = "list-group">
                        <li class = 'bg-secondary list-group-item'><strong>BRL: </strong>{{ BRL }}</li>
                        <li class = 'bg-secondary list-group-item'><strong>USD: </strong>{{ USD }}</li>
                        <li class = 'bg-secondary list-group-item'><strong>EUR: </strong>{{ EUR }}</li>
                  </ul>
            </div>
      </div>
</template>

