<template>
    <div class="home">
      <div class="container">
        <div>Polkadot</div>
        <!-- <h1 class="intro">Welcome to Crypto Marketplace</h1> -->
      </div>
    </div>
    <div>{{ cryptos.CHANGE24HOUR }}</div>
    <div>{{ cryptos.CHANGEDAY }}</div>
    <div>{{ cryptos.CHANGEHOUR }}</div>
    <div>{{ cryptos.CHANGEPCT24HOUR }}</div>
    <div>{{ cryptos.CHANGEPCTDAY }}</div>
    <div>{{ cryptos.CHANGEPCTHOUR }}</div>
    <div>{{ cryptos.CIRCULATINGSUPPLY }}</div>
    <div>{{ cryptos.CIRCULATINGSUPPLYMKTCAP }}</div>
    <div>{{ cryptos.OPENDAY }}</div>
    <div>{{ cryptos.OPENHOUR }}</div>
    <div>{{ cryptos.VOLUME24HOUR }}</div>
    <div>{{ cryptos.VOLUME24HOURTO }}</div>
    <div>{{ cryptos.VOLUMEDAY }}</div>
    <div>{{ cryptos.VOLUMEDAYTO }}</div>
    <div>{{ cryptos.VOLUMEHOUR }}</div>
    <div>{{ cryptos.VOLUMEHOURTO }}</div>
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
        this.cryptos = response.data.RAW.DOT.USD;
        console.log(response.data);
        console.log(response.data.RAW.DOT.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>