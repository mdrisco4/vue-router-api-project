<template>
    <div class="home">
      <div class="container">
        <div>BITCOIN</div>
        <!-- <h1 class="intro">Welcome to Crypto Marketplace</h1> -->
      </div>
    </div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CHANGE24HOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CHANGEDAY }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CHANGEHOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CHANGEPCT24HOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CHANGEPCTDAY }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CHANGEPCTHOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CIRCULATINGSUPPLY }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.CIRCULATINGSUPPLYMKTCAP }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.OPENDAY }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.OPENHOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.VOLUME24HOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.VOLUME24HOURTO }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.VOLUMEDAY }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.VOLUMEDAYTO }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.VOLUMEHOUR }}</div>
    <div class="data-label">Label</div>
    <div class="data-value">{{ cryptos.VOLUMEHOURTO }}</div>
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
        this.cryptos = response.data.RAW.BTC.USD;
        console.log(response.data);
        console.log(response.data.RAW.BTC.USD.CHANGE24HOUR);
        console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>