 <script>
     export default {
         name: "Nav"
     }
 </script>

 <template>
    <nav class = 'px-1 navbar-expand bg-secondary'>
        <img class = 'h-100' src = "https://static.coingecko.com/s/coingecko-mascot-suit-b1a9df2b041094a017948f1d184f1aa263e779d4e1f22c437e835b74f0b00073.png" ><span class = 'fs-3'>CriptoCurrency</span>
        <select class="text-white form-select bg-secondary w-25 d-inline mx-3" aria-label="Default select example">
            <option hidden disabled selected>CHOOSE YOUR CRIPTO HERE</option>
            <option name = 'bitcoin' value="1">Bitcoin</option>
            <option name = 'ethereum' value="2">ETH</option>
            <option name = 'dacxi' value="3">DACXI</option>
            <option name = 'cosmos' value="3">ATOM</option>
            <option name = 'terra-luna' value="3">LUNA</option>
        </select>
        <span class = 'fs-5'> VS </span>
        <select class="text-white form-select bg-secondary w-25 d-inline mx-3" aria-label="Default select example">
            <option hidden disabled selected>CHOOSE YOUR VS CURRENT HERE</option>
            <option class = 'text-uppercase' value="1">brl</option>
            <option class = 'text-uppercase' value="2">usb</option>
            <option class = 'text-uppercase' value="3">eur</option>
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
