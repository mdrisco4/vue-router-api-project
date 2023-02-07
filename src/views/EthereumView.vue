<template>
    <div class="container">
    <div class="title">Ethereum</div>
    <div class="intro-information">Some information and a blurb about coin X</div>
    </div>
    <div class="data-label">24-Hour Change</div>
    <div class="data-value">{{ cryptos.CHANGE24HOUR }}</div>
    <div class="data-label">Change Today</div>
    <div class="data-value">{{ cryptos.CHANGEDAY }}</div>
    <div class="data-label">1-Hour Change</div>
    <div class="data-value">{{ cryptos.CHANGEHOUR }}</div>
    <div class="data-label">24-Hour % Change</div>
    <div class="data-value">{{ cryptos.CHANGEPCT24HOUR }}</div>
    <div class="data-label">Change % Today</div>
    <div class="data-value">{{ cryptos.CHANGEPCTDAY }}</div>
    <div class="data-label">1-Hour % Change</div>
    <div class="data-value">{{ cryptos.CHANGEPCTHOUR }}</div>
    <div class="data-label">Total Supply</div>
    <div class="data-value">{{ cryptos.CIRCULATINGSUPPLY }}</div>
    <div class="data-label">Market Cap</div>
    <div class="data-value">{{ cryptos.CIRCULATINGSUPPLYMKTCAP }}</div>
    <div class="data-label">Daily Opening</div>
    <div class="data-value">{{ cryptos.OPENDAY }}</div>
    <div class="data-label">Hourly Opening</div>
    <div class="data-value">{{ cryptos.OPENHOUR }}</div>
    <div class="data-label">24-Hour Volume</div>
    <div class="data-value">{{ cryptos.VOLUME24HOUR }}</div>
    <div class="data-label">--unknown--</div>
    <div class="data-value">{{ cryptos.VOLUME24HOURTO }}</div>
    <div class="data-label">Daily Volume</div>
    <div class="data-value">{{ cryptos.VOLUMEDAY }}</div>
    <div class="data-label">--unknown--</div>
    <div class="data-value">{{ cryptos.VOLUMEDAYTO }}</div>
    <div class="data-label">Hourly Volume</div>
    <div class="data-value">{{ cryptos.VOLUMEHOUR }}</div>
    <div class="data-label">--unknown--</div>
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
        this.cryptos = response.data.RAW.ETH.USD;
        console.log(response.data);
        console.log(response.data.RAW.ETH.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<style>
.title {
  font-size: 30px;
}

.intro-information {
  font-size: 24px;
}

.data-label {
  font-size: 20px;
}

.data-value {
  font-size: 20px; 
}

</style>