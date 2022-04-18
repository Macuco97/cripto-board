 <script>
     export default {
         name: "Nav",
         data() {
             return {
                 chosenCripto: "CHOOSE YOUR CRIPTO HERE",
                 chosenVS: "CHOOSE YOUR VS CURRENT HERE" 
             }
         },

         watch: {
             chosenCripto() {
                 this.$emit('setChosenCripto', this.chosenCripto)
             },
             chosenVS() {
                 this.$emit('setChosenVS', this.chosenVS)
             }
             
         }
         
     }
 </script>

 <template>
    <nav class = 'px-1 navbar-expand bg-secondary'>
        <img class = 'h-100' src = "https://static.coingecko.com/s/coingecko-mascot-suit-b1a9df2b041094a017948f1d184f1aa263e779d4e1f22c437e835b74f0b00073.png" ><span class = 'fs-3'>CriptoCurrency</span>
        <select v-model = 'chosenCripto' class="text-white form-select bg-secondary w-25 d-inline mx-3" aria-label="Default select example">
            <option hidden disabled selected>CHOOSE YOUR CRIPTO HERE</option>
            <option value="bitcoin">Bitcoin</option>
            <option value="ethereum">ETH</option>
            <option value="dacxi">DACXI</option>
            <option value="cosmos">ATOM</option>
            <option value="terra-luna">LUNA</option>
        </select>
        <span class = 'fs-5'> VS </span>
        <select v-model = 'chosenVS' class="text-white form-select bg-secondary w-25 d-inline mx-3" aria-label="Default select example">
            <option hidden disabled selected>CHOOSE YOUR VS CURRENT HERE</option>
            <option class = 'text-uppercase' value="brl">BRL</option>
            <option class = 'text-uppercase' value="usd">USD</option>
            <option class = 'text-uppercase' value="eur">EUR</option>
        </select>
        <input type = 'date' class = 'w-25 text-white d-inline bg-secondary form-control'>


    </nav> 
 </template>

 <style>
    img { 
         height: 30px;
         width: 30px;
         position: relative;
         bottom: 5px;
        }
 </style>
