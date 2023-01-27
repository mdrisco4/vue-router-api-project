<template>
  <div class="additional">
      <div id="column-titles">
          <span class="left">Coin</span>
          <span class="middle-left">Dily Low</span>
          <span class="middle-right">Daily High</span>
          <span class="right">Current</span>
        </div>
    <div
      id="crypto-container"
      v-for="(item, index) in cryptos"
      v-bind:key="index"
    >
    <div>
        <span class="left">{{ item.USD.FROMSYMBOL }}</span>
        <span class="middle-left">{{ item.USD.LOWDAY }}</span>
        <span class="middle-right">{{ item.USD.HIGHDAY }}</span>
        <span class="right">${{ item.USD.PRICE }}</span>
    </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CryptoApp",
  data: () => ({
    cryptos: [],
    errors: [],
  }),

  created() {
    axios
      .get(
        "https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,XRP,ADA,DOGE,MATIC,SOL,DOT,SHIB.LTC,TRX,ATOM,LNK,ETC&tsyms=USD"
      )
      // IOT
      // ,EUR
      .then((response) => {
        this.cryptos = response.data.RAW;
        console.log(response.data);
        console.log(response.data.DISPLAY.BTC.USD.PRICE);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<style>
body {
    background-color: #f1f1f1;
}

div#column-titles {
    background-color: lightblue;
    width: 70%;
    margin: 0 auto 4px auto;
    padding: 1em;
    box-shadow: 1px 1px 0 lightgray;
    font-weight: 800;
    text-decoration: underline;
}

div#crypto-container {
    background-color: white;
    width: 70%;
    margin: 0 auto 4px auto;
    padding: 1em;
    box-shadow: 1px 1px 0 lightgray;
}

span.left {
    font-weight: 500;
}

span.middle-left {
    padding-left: 25%;
}

span.middle-right {
    padding-left: 25%;
}

span.right {
    float:right;
}

</style>
