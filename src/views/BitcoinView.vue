<template>
  <div class="coins-links-container">
    <router-link to="/Bitcoin" class="coin-page-link" exact-active-class="exact-active-link"> BTC </router-link>|
    <router-link to="/Ethereum" class="coin-page-link" exact-active-class="exact-active-link"> ETH </router-link>|
    <router-link to="/XRP" class="coin-page-link" exact-active-class="exact-active-link"> XRP </router-link>|
    <router-link to="/Cardano" class="coin-page-link" exact-active-class="exact-active-link"> ADA </router-link>|
    <router-link to="/Dogecoin" class="coin-page-link" exact-active-class="exact-active-link"> DOGE </router-link>|
    <router-link to="Polygon" class="coin-page-link" exact-active-class="exact-active-link"> MATIC </router-link>|
    <router-link to="/Solana" class="coin-page-link" exact-active-class="exact-active-link"> SOL </router-link>|
    <router-link to="/Polkadot" class="coin-page-link" exact-active-class="exact-active-link"> DOT </router-link>|
    <router-link to="/Tron" class="coin-page-link" exact-active-class="exact-active-link"> TRX </router-link>|
    <router-link to="/Cosmos" class="coin-page-link" exact-active-class="exact-active-link"> ATOM </router-link>|
    <router-link to="/Chainlink" class="coin-page-link" exact-active-class="exact-active-link"> LNK </router-link>|
    <router-link to="/EthereumClassic" class="coin-page-link" exact-active-class="exact-active-link">ETC</router-link>
  </div>
  <div class="coin-page-container">
    <div class="title">BITCOIN</div>
    <div class="intro-information">
      Bitcoin (BTC) is a cryptocurrency, a virtual currency designed to act as
      money and a form of payment outside the control of any one person, group,
      or entity, thus removing the need for third-party involvement in financial
      transactions. It is rewarded to blockchain miners for the work done to
      verify transactions and can be purchased on several exchanges.
    </div>
    <div class="intro-information">
      Bitcoin was introduced to the public in 2009 by an anonymous developer or
      group of developers using the name Satoshi Nakamoto.
    </div>
    <div class="intro-information">
      It has since become the most well-known cryptocurrency in the world. Its
      popularity has inspired the development of many other cryptocurrencies.
      These competitors either attempt to replace it as a payment system or are
      used as utility or security tokens in other blockchains and emerging
      financial technologies.
    </div>
  </div>
  <div class="overall-data-container">
    <div class="stats-column-container">
      <div class="individual-stat-container">
        <div class="data-label">24-Hour Change</div>
        <div class="data-value">{{ cryptos.CHANGE24HOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Change Today</div>
        <div class="data-value">{{ cryptos.CHANGEDAY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">1-Hour Change</div>
        <div class="data-value">{{ cryptos.CHANGEHOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">24-Hour % Change</div>
        <div class="data-value">{{ cryptos.CHANGEPCT24HOUR }}</div>
      </div>
    </div>
    <div class="stats-column-container">
      <div class="individual-stat-container">
        <div class="data-label">Change % Today</div>
        <div class="data-value">{{ cryptos.CHANGEPCTDAY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">1-Hour % Change</div>
        <div class="data-value">{{ cryptos.CHANGEPCTHOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Total Supply</div>
        <div class="data-value">{{ cryptos.CIRCULATINGSUPPLY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Market Cap</div>
        <div class="data-value">{{ cryptos.CIRCULATINGSUPPLYMKTCAP }}</div>
      </div>
    </div>
    <div class="stats-column-container">
      <div class="individual-stat-container">
        <div class="data-label">Daily Opening</div>
        <div class="data-value">{{ cryptos.OPENDAY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Hourly Opening</div>
        <div class="data-value">{{ cryptos.OPENHOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">24-Hour Volume</div>
        <div class="data-value">{{ cryptos.VOLUME24HOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">--unknown--</div>
        <div class="data-value">{{ cryptos.VOLUME24HOURTO }}</div>
      </div>
    </div>
    <div class="stats-column-container">
      <div class="individual-stat-container">
        <div class="data-label">Daily Volume</div>
        <div class="data-value">{{ cryptos.VOLUMEDAY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">--unknown--</div>
        <div class="data-value">{{ cryptos.VOLUMEDAYTO }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Hourly Volume</div>
        <div class="data-value">{{ cryptos.VOLUMEHOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">--unknown--</div>
        <div class="data-value">{{ cryptos.VOLUMEHOURTO }}</div>
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
        this.cryptos = response.data.RAW.BTC.USD;
        console.log(response.data);
        console.log(response.data.RAW.BTC.USD.CHANGE24HOUR);
        console.log(this.cryptos);
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<style>
.coins-links-container {
  display: flex;
  flex-direction: row;
  background-color: black;
  justify-content: center;
  color: white;
  font-size: 8px;
}

@media only screen and (min-width: 500px) {
  .coins-links-container {
    font-size: 12px;
  }
}

@media only screen and (min-width: 625px) {
  .coins-links-container {
    font-size: 16px;
  }
}

@media only screen and (min-width: 768px) {
  .coins-links-container {
    font-size: 20px;
  }
}

@media only screen and (min-width: 900px) {
  .coins-links-container {
    font-size: 25px;
  }
}

@media only screen and (min-width: 1050px) {
  .coins-links-container {
    font-size: 32px;
  }
}

.coin-page-link {
  text-decoration: none;
  font-weight: bold;
  padding-left: 4px;
  padding-right: 4px;
  font-size: 8px;
  color: white;
}

@media only screen and (min-width: 500px) {
  .coin-page-link {
    font-size: 12px;
  }
}

@media only screen and (min-width: 625px) {
  .coin-page-link {
    font-size: 16px;
  }
}

@media only screen and (min-width: 768px) {
  .coin-page-link {
    font-size: 20px;
  }
}

@media only screen and (min-width: 900px) {
  .coin-page-link {
    font-size: 25px;
  }
}

@media only screen and (min-width: 1050px) {
  .coin-page-link {
    font-size: 32px;
  }
}

.coin-page-link:hover {
  color: yellow;
}

.exact-active-link {
  color: greenyellow;;
}

.coin-page-container {
  background-color: aqua;
}

.title {
  font-size: 30px;
  text-align: center;
}

@media only screen and (min-width: 500px) {
  .title {
    font-size: 35px;
  }
}

@media only screen and (min-width: 625px) {
  .title {
    font-size: 42px;
  }
}

@media only screen and (min-width: 768px) {
  .title {
    font-size: 48px;
  }
}

@media only screen and (min-width: 980px) {
  .title {
    font-size: 54px;
  }
}

.intro-information {
  font-size: 8px;
  text-align: center;
  width: 90%;
  margin: 0 5% 0 5%;
}

@media only screen and (min-width: 500px) {
  .intro-information {
    font-size: 10px;
  }
}

@media only screen and (min-width: 625px) {
  .intro-information {
    font-size: 12px;
  }
}

@media only screen and (min-width: 768px) {
  .intro-information {
    font-size: 15px;
  }
}

@media only screen and (min-width: 980px) {
  .intro-information {
    font-size: 18px;
  }
}

.data-label {
  font-size: 12px;
  text-align: center;
  background-color: aqua;
}

@media only screen and (min-width: 500px) {
  .data-label {
    font-size: 16px;
  }
}

@media only screen and (min-width: 625px) {
  .data-label {
    font-size: 20px;
  }
}

@media only screen and (min-width: 768px) {
  .data-label {
    font-size: 16px;
  }
}

@media only screen and (min-width: 980px) {
  .data-label {
    font-size: 24px;
  }
}

.data-value {
  font-size: 12px;
  text-align: center;
  background-color: aqua;
}

@media only screen and (min-width: 500px) {
  .data-value {
    font-size: 16px;
  }
}

@media only screen and (min-width: 625px) {
  .data-value {
    font-size: 20px;
  }
}

@media only screen and (min-width: 768px) {
  .data-value {
    font-size: 16px;
  }
}

@media only screen and (min-width: 980px) {
  .data-value {
    font-size: 24px;
  }
}

.overall-data-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border-top: 12px solid aqua;
  border-bottom: 200px solid aqua;
}

@media only screen and (min-width: 500px) {
  .overall-data-container {
    border-top: 15px solid aqua;
  }
}

@media only screen and (min-width: 625px) {
  .overall-data-container {
    border-top: 18px solid aqua;
  }
}

@media only screen and (min-width: 768px) {
  .overall-data-container {
    grid-template-columns: 1fr 1fr 1fr 1fr;
    border-top: 27px solid aqua;
  }
}

@media only screen and (min-width: 980px) {
  .overall-data-container {
    border-top: 32px solid aqua;
  }
}

.stats-column-container {
  /* width: 25%; */
}

@media only screen and (min-width: 500px) {
  .stats-column-container {
  }
}

@media only screen and (min-width: 625px) {
  .stats-column-container {
  }
}

@media only screen and (min-width: 768px) {
  .stats-column-container {
  }
}

@media only screen and (min-width: 980px) {
  .stats-column-container {
  }
}

.individual-stat-container {
}

@media only screen and (min-width: 500px) {
  .individual-stat-container {
  }
}

@media only screen and (min-width: 625px) {
  .individual-stat-container {
  }
}

@media only screen and (min-width: 768px) {
  .individual-stat-container {
  }
}

@media only screen and (min-width: 980px) {
  .individual-stat-container {
  }
}
</style>
