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
    <div class="title">Solana</div>
    <div class="intro-information">
      Solana (CRYPTO:SOL) is a blockchain platform known for its speed and
      efficiency. SOL tokens are its native cryptocurrency and are used to pay
      its transaction fees. Since launching in 2017, Solana has grown to become
      one of the largest cryptocurrencies in the world.
    </div>
    <div class="intro-information">
      Because the Solana blockchain has smart contract capability, developers
      can use it to build decentralized apps (dApps). Its strong growth has
      helped establish it as a rival to other major programmable blockchains,
      including Ethereum (CRYPTO:ETH) and Cardano (CRYPTO:ADA).
    </div>
    <div class="intro-information">
      Solana is in a competitive marketplace, but there are several reasons to
      be bullish on it. Read on for a detailed guide to Solana to learn more and
      decide if you should invest.
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
        this.cryptos = response.data.RAW.SOL.USD;
        console.log(response.data);
        console.log(response.data.RAW.SOL.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
