<template>
  <div class="additional">
      <div id="column-titles">
          <div class="left">Coin</div>
          <div class="middle-left">Daily Low</div>
          <div class="middle-right">Daily High</div>
          <div class="right">Current</div>
        </div>
    <div
      id="crypto-container"
      v-for="(item, index) in cryptos"
      v-bind:key="index"
    >
        <div class="left">{{ item.USD.FROMSYMBOL }}</div>
        <div class="middle-left">{{ item.USD.LOWDAY }}</div>
        <div class="middle-right">{{ item.USD.HIGHDAY }}</div>
        <div class="right">${{ item.USD.PRICE }}</div>
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
    display: flex;
}

div#crypto-container {
    background-color: white;
    width: 70%;
    margin: 0 auto 4px auto;
    padding: 1em;
    box-shadow: 1px 1px 0 lightgray;
    display: flex;
}

div.left {
    font-weight: 500;
    width: 20%;
}

div.middle-left {
    width: 27.5%;
    text-align: right;
    /* padding-left: 25%; */
}

div.middle-right {
    width: 27.5%;
    text-align: right;
    /* padding-left: 25%; */
}

div.right {
    width: 25%;
    text-align: right;
    /* float:right; */
}

</style>
