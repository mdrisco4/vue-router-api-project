  <template>
    <div class="additional">
      <!-- <div id="crypto-container" v-for="(value, key) in cryptos"> -->
        <div id="crypto-container" v-bind:key="(value, key) in cryptos">
        <span class="left">{{ key }}</span>
        <span class="left">${{ value }}</span>
    </div>
    </div>
  </template>




  <script>
    import axios from 'axios';

    export default {
        name: 'crypto-app',
        data: () => ({
            cryptos: [],
            errors: []
        }),

        created () {
            axios.get('https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,XRP&tsyms=USD')
            // IOT
            // ,EUR
            .then(response => {
                this.cryptos = response.data.DISPLAY
                // console.log(response.data.DISPLAY)
                console.log(this.cryptos)
            })
            .catch(e => {
                this.errors.push(e)
            })
        }
    }

  </script>



  <style>

  </style>







// import axios from "axios";


// export default {
//     data() {
//         return {
//             res: [],
//         };
//     },
//     name: "App",
//     methods: {
//         // The get method called by the function
//         onGet() {
//             axios
//                 // .get("https://jsonplaceholder.typicode.com/todos")
//                 .get("http://api.coinlayer.com/live?access_key=bcdeb65136f7fd4dfe6f4860168e9211")
//                 .then((response) => {
//                     console.log(response);
//                     // using stringify to beautify the output
//                     this.res = JSON.stringify(response.data);
//                 })
//                 .catch((errors) => {
//                     console.log(errors); // Errors
//                 });
//         },
//     },
// };



// export default {
//   name: "HomeView",
//   data() {
//     return {
//       list: [],
//     };
//   },

//   async mounted() {
//     // let result = await axios.get("https://rest.coinapi.io/v1/quotes/latest");
//     // let result = await axios.get("https://api.coinranking.com/v2");

//     // let result = await axios.get("https://api.coinranking.com/v2/coins");

//     // let result = await axios.get("http://api.coinlayer.com/live?access_key=bcdeb65136f7fd4dfe6f4860168e9211");

//     let result = await axios.get("https://reqres.in/api/users?page=1");
//     console.log(result.data.data);
//     this.list = result.data.data;
//   },
// };