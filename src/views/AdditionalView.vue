<template>
  <div class="additional">
    <div id="column-titles">
      <div class="left">Coin</div>
      <div class="middle-left">Daily Low</div>
      <div class="middle-right">Daily High</div>
      <div class="right">Current</div>
    </div>
    <div class="overall-comtainer">
      <div class="coins-container">
        <router-link to="/Bitcoin" class="coin-links">
          <div class="coin-title">BTC</div>
        </router-link>
        <router-link to="/Ethereum" class="coin-links">
          <div class="coin-title">ETH</div>
        </router-link>
        <router-link to="/XRP" class="coin-links">
          <div class="coin-title">XRP</div>
        </router-link>
        <router-link to="/Cardano" class="coin-links">
          <div class="coin-title">ADA</div>
        </router-link>
        <router-link to="/Dogecoin" class="coin-links">
          <div class="coin-title">DOGE</div>
        </router-link>
        <router-link to="Polygon" class="coin-links">
          <div class="coin-title">MATIC</div>
        </router-link>
        <router-link to="/Solana" class="coin-links">
          <div class="coin-title">SOL</div>
        </router-link>
        <router-link to="/Polkadot" class="coin-links">
          <div class="coin-title">DOT</div>
        </router-link>
        <router-link to="/Tron" class="coin-links">
          <div class="coin-title">TRX</div>
        </router-link>
        <router-link to="/Cosmos" class="coin-links">
          <div class="coin-title">ATOM</div>
        </router-link>
        <router-link to="/Chainlink" class="coin-links">
          <div class="coin-title">LNK</div>
        </router-link>
        <router-link to="/EthereumClassic" class="coin-links">
          <div class="coin-title">ETC</div>
        </router-link>
      </div>
      <div class="loop-container">

        <div
          id="crypto-container"
          v-for="(item, index) in cryptos"
          v-bind:key="index"
        >
          <!-- <div class="loop-left">{{ item.USD.FROMSYMBOL }}</div> -->
          <div class="loop-left">${{ item.USD.LOWDAY }}</div>
          <div class="loop-middle">${{ item.USD.HIGHDAY }}</div>
          <div class="loop-right">${{ item.USD.PRICE }}</div>
        </div>
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
        // console.log(response.data);
        // console.log(response.data.DISPLAY.BTC.USD.PRICE);

        
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
  color: white;
  background-color: black;
  width: 70%;
  margin: 0 auto 0 auto;
  border: 1em 1em 0 1em solid black;
  /* box-shadow: 1px 1px 0 lightgray; */
  font-weight: 800;
  text-decoration: underline;
  display: flex;
}

div.left {
  font-weight: 500;
  width: 20%;
  font-size: 12px;
}

@media only screen and (min-width: 500px) {
  div.left {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.left {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.left {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.left {
    font-size: 32px;
  }
}

div.middle-left {
  width: 27.5%;
  text-align: right;
  font-size: 12px;
  /* padding-left: 25%; */
}

@media only screen and (min-width: 500px) {
  div.middle-left {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.middle-left {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.middle-left {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.middle-left {
    font-size: 32px;
  }
}

div.middle-right {
  width: 27.5%;
  text-align: right;
  font-size: 12px;
  /* padding-left: 25%; */
}

@media only screen and (min-width: 500px) {
  div.middle-right {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.middle-right {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.middle-right {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.middle-right {
    font-size: 32px;
  }
}

div.right {
  width: 25%;
  text-align: right;
  font-size: 12px;
  /* float:right; */
}

@media only screen and (min-width: 500px) {
  div.right {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.right {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.right {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.right {
    font-size: 32px;
  }
}

div.overall-container {
  display: flex;
  flex-direction: row;
}

div.coins-container {
  width: 20%;
  float: left;
  border-left: 13.5vw solid black;
  /* border-left: 14%;
  border-left-color: black; */
}

div.coin-title {
  color: white;
  background-color: black;
  margin: 0 auto 4px auto;
  padding: 16px;
  /* box-shadow: 1px 1px 0 lightgray; */
  height: 40px;
  font-size: 12px;
}

@media only screen and (min-width: 500px) {
  div.coin-title {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.coin-title {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.coin-title {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.coin-title {
    font-size: 32px;
  }
}

.coin-links {
  text-decoration: none;
  font-weight: bold;
  color: black;
}

.coin-links:hover {
  color: red;
}

.loop-container {
  width: 52%;
  float: right;
  /* margin-right: 14%; */
  border-right: 13.5vw solid black;
}

div#crypto-container {
  color: white;
  background-color: black;
  margin: 0 auto 4px auto;
  padding: 1em;
  /* box-shadow: 1px 1px 0 lightgray; */
  display: flex;
  height: 40px;
}

div.loop-left {
  /* color: white;
  background-color: black; */
  width: 33.3%;
  text-align: right;
  /* padding-right: 10%; */
  font-size: 9px;
  overflow: hidden;
  max-width: 9.5ch;
}

@media only screen and (min-width: 400px) {
  div.loop-left {
    font-size: 12px;
  }
}

@media only screen and (min-width: 500px) {
  div.loop-left {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.loop-left {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.loop-left {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.loop-left {
    font-size: 32px;
  }
}

div.loop-middle {
  width: 33.3%;
  text-align: right;
  /* padding-right: 6%; */
  font-size: 9px;
}

@media only screen and (min-width: 400px) {
  div.loop-middle {
    font-size: 12px;
  }
}

@media only screen and (min-width: 500px) {
  div.loop-middle {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.loop-middle {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.loop-middle {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.loop-middle {
    font-size: 32px;
  }
}

div.loop-right {
  width: 33.3%;
  text-align: right;
  /* padding-right: 2%; */
  font-size: 9px;
}

@media only screen and (min-width: 400px) {
  div.loop-right {
    font-size: 12px;
  }
}

@media only screen and (min-width: 500px) {
  div.loop-right {
    font-size: 15px;
  }
}

@media only screen and (min-width: 625px) {
  div.loop-right {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  div.loop-right {
    font-size: 24px;
  }
}

@media only screen and (min-width: 980px) {
  div.loop-right {
    font-size: 32px;
  }
}
</style>
