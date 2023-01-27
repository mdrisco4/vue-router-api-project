<template>
  <div class="additional">
    <!-- <div id="crypto-container" v-for="(value, key) in cryptos"> -->
    <!-- <div id="crypto-container" v-bind:key="item in cryptos"> -->
    <div
      id="crypto-container"
      v-for="(item, index) in cryptos"
      v-bind:key="index"
    >
      <span class="left">${{ item.USD.FROMSYMBOL }}</span>
      <span class="left">{{ item.USD.PRICE }}</span>
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
        "https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,XRP&tsyms=USD"
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

<style></style>
