 <script>
     export default {
         name: "Nav",
         data() {
             return {
                 chosenCripto: "Choose your cripto",
                 showMenu: false
             }
         },

         methods: {
             showOffcanvasMenu(){
                this.showMenu ? this.showMenu = false : this.showMenu = true;
        }
         },
         
         watch: {
             chosenCripto() {
                 this.$emit('setChosenCripto', this.chosenCripto)
             }           
         }
         
     }
 </script>

 <template>
     <div id="app" class="container py-2">
        <nav class="navbar d-inline  navbar-collapse navbar-dark fixed-top">
            <div class="container">
                <span class="float-start">
                    <button class="navbar-toggler" type="button" @click.prevent="showOffcanvasMenu()">
                        <span class="navbar-toggler-icon"></span>
                    </button>
                </span>
            </div>
            <div class="offcanvas bg-secondary offcanvas-start" :class="showMenu ? 'show' : ''" tabindex="-1" :style="{ visibility: showMenu ? 'visible' : 'hidden' }">
                <div class="offcanvas-header">
                    <h5 class="offcanvas-title" id="">Choose your options below</h5>
                    <button type="button" class="btn-close bg-light text-reset" @click.prevent="showOffcanvasMenu()"></button>
                </div>
                <div class="offcanvas-body">
                    <div class="input-group mb-3">
                        <label class="input-group-text" for="inputGroupSelect01">Options</label>
                        <select v-model = 'chosenCripto' class="form-select" id="inputGroupSelect01">
                            <option hidden selected>Choose your cripto</option>
                            <option value="bitcoin">Bitcoin</option>
                            <option value="dacxi">DACXI</option>
                            <option value="ethereum">Ethereum</option>
                            <option value="cosmos">ATOM</option>
                            <option value="terra-luna">LUNA</option>
                        </select>
                    </div>
                    <input class = 'form-select' id = 'inputDate' type = 'date'/>
                </div>
            </div>
        </nav>
    </div>
 </template>

