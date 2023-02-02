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
        <router-link to="/Bitcoin">
          <div class="coin-title">BTC</div>
        </router-link>
        <router-link to="/Ethereum">
          <div class="coin-title">ETH</div>
        </router-link>
        <router-link to="/XRP">
          <div class="coin-title">XRP</div>
        </router-link>
        <router-link to="/Cardano">
          <div class="coin-title">ADA</div>
        </router-link>
        <router-link to="/Dogecoin">
          <div class="coin-title">DOGE</div>
        </router-link>
        <router-link to="Polygon">
          <div class="coin-title">MATIC</div>
        </router-link>
        <router-link to="/Solana">
          <div class="coin-title">SOL</div>
        </router-link>
        <router-link to="/Polkadot">
          <div class="coin-title">DOT</div>
        </router-link>
        <router-link to="/Tron">
          <div class="coin-title">TRX</div>
        </router-link>
        <router-link to="/Cosmos">
          <div class="coin-title">ATOM</div>
        </router-link>
        <router-link to="/Chainlink">
          <div class="coin-title">LNK</div>
        </router-link>
        <router-link to="/EthereumClassic">
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
          <div class="loop-left">{{ item.USD.LOWDAY }}</div>
          <div class="loop-middle">{{ item.USD.HIGHDAY }}</div>
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
  margin-left: 14%;
}

div.coin-title {
  background-color: white;
  margin: 0 auto 4px auto;
  padding: 16px;
  box-shadow: 1px 1px 0 lightgray;
  height: 40px;
  font-size: 28px;
}

.loop-container {
  width: 52%;
  float: right;
  margin-right: 14%;
}

div#crypto-container {
  background-color: white;
  margin: 0 auto 4px auto;
  padding: 1em;
  box-shadow: 1px 1px 0 lightgray;
  display: flex;
  height: 40px;
}

div.loop-left {
  width: 33.3%;
  text-align: right;
  padding-right: 10%;
  font-size: 32px;
}

div.loop-middle {
  width: 33.3%;
  text-align: right;
  padding-right: 6%;
  font-size: 32px;
}

div.loop-right {
  width: 33.3%;
  text-align: right;
  padding-right: 2%;
  font-size: 32px;
}
</style>
