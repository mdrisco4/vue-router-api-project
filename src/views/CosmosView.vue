<template>
  <div class="coins-links-container">
    <router-link to="/Bitcoin" class="coin-page-link"> BTC </router-link>|
    <router-link to="/Ethereum" class="coin-page-link"> ETH </router-link>|
    <router-link to="/XRP" class="coin-page-link"> XRP </router-link>|
    <router-link to="/Cardano" class="coin-page-link"> ADA </router-link>|
    <router-link to="/Dogecoin" class="coin-page-link"> DOGE </router-link>|
    <router-link to="Polygon" class="coin-page-link"> MATIC </router-link>|
    <router-link to="/Solana" class="coin-page-link"> SOL </router-link>|
    <router-link to="/Polkadot" class="coin-page-link"> DOT </router-link>|
    <router-link to="/Tron" class="coin-page-link"> TRX </router-link>|
    <router-link to="/Cosmos" class="coin-page-link"> ATOM </router-link>|
    <router-link to="/Chainlink" class="coin-page-link"> LNK </router-link>|
    <router-link to="/EthereumClassic" class="coin-page-link">ETC</router-link>
  </div>
  <div class="coin-page-container">
    <div class="title">Cosmos</div>
    <div class="intro-information">
      The Cosmos (ATOM) network is an ecosystem of blockchains that can scale
      and interoperate. Cosmos seeks to create an Internet of Blockchains
      through which blockchains can maintain sovereignty, interact with other
      blockchains in the ecosystem, and process transactions quickly–making it
      optimal for multiple use cases. The network functions using BFT consensus
      algorithms along with Tendermint consensus, which is used to power each
      blockchain in the Cosmos. Tendermint BFT is a proof-of-stake consensus
      protocol that powers the Cosmos Hub and the Cosmos SDK (software
      development kit). BFT (Byzantine fault tolerance) is a consensus algorithm
      of a distributed network that reaches consensus even when some of the
      network’s nodes respond with incorrect information or fail to respond.
    </div>
    <div class="intro-information">
      The Cosmos SDK is an open-source framework that aims to build multi-asset
      public proof-of-stake (PoS) blockchains. The Cosmos Hub is a blockchain
      that serves as the economic center of the Cosmos platform. The Cosmos Hub
      aims to provide interchain token exchange, interchain security, bridges to
      ETH and BTC, and interchain token custodianship.
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
        this.cryptos = response.data.RAW.ATOM.USD;
        console.log(response.data);
        console.log(response.data.RAW.ATOM.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
