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
    <div class="title">Cardano</div>
    <div class="intro-information">
      Cardano is a proof-of-stake blockchain platform: the first to be founded
      on peer-reviewed research and developed through evidence-based methods. It
      combines pioneering technologies to provide unparalleled security and
      sustainability to decentralized applications, systems, and societies.
    </div>
    <div class="intro-information">
      With a leading team of engineers, Cardano exists to redistribute power
      from unaccountable structures to the margins – to individuals – and be an
      enabling force for positive change and progress.
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
        <div class="data-label">Hourly Volume</div>
        <div class="data-value">{{ cryptos.VOLUMEHOUR }}</div>
      </div>
    </div>
    <div class="stats-column-container">
      <div class="individual-stat-container">
        <div class="data-label">High Day</div>
        <div class="data-value">{{ cryptos.HIGHDAY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">High Hour</div>
        <div class="data-value">{{ cryptos.HIGHHOUR }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Daily Volume</div>
        <div class="data-value">{{ cryptos.VOLUMEDAY }}</div>
      </div>
      <div class="individual-stat-container">
        <div class="data-label">Median</div>
        <div class="data-value">{{ cryptos.MEDIAN }}</div>
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
        this.cryptos = response.data.RAW.ADA.USD;
        console.log(response.data);
        console.log(response.data.RAW.ADA.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
