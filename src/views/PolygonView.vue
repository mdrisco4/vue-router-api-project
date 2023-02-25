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
    <div class="title">Polygon</div>
    <div class="intro-information">
      The Ethereum blockchain is home to a vast range of economic activity —
      from NFT markets and games to the growing DeFi ecosystem. Ethereum is well
      suited to this activity because it’s compatible with smart contracts,
      which can be used to build a vast range of applications.
    </div>
    <div class="intro-information">
      However, the growing popularity of these applications adds many
      transactions to the Ethereum blockchain — and as a result, transaction
      fees (also known as “gas”) can sometimes rise to the point where making
      small or frequent investments can be economically unviable.
    </div>
    <div class="intro-information">
      Enter Polygon, which is a “Layer 2” scaling solution (or “sidechain”)
      that’s emerged to provide faster transactions and lower costs for users.
      It acts as a speedy parallel blockchain running alongside the main
      Ethereum blockchain. To use it, you can “bridge” some of your crypto over
      to Polygon, and then interact with a wide range of popular crypto apps
      that were once exclusive to the main Ethereum blockchain.
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
        this.cryptos = response.data.RAW.MATIC.USD;
        console.log(response.data);
        console.log(response.data.RAW.MATIC.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
