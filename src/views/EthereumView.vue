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
    <div class="title">Ethereum</div>
    <div class="intro-information">
      Ethereum is a decentralized blockchain platform that establishes a
      peer-to-peer network that securely executes and verifies application code,
      called smart contracts. Smart contracts allow participants to transact
      with each other without a trusted central authority. Transaction records
      are immutable, verifiable, and securely distributed across the network,
      giving participants full ownership and visibility into transaction data.
      Transactions are sent from and received by user-created Ethereum accounts.
      A sender must sign transactions and spend Ether, Ethereum's native
      cryptocurrency, as a cost of processing transactions on the network.
    </div>
    <div class="intro-information">
      Ethereum offers an extremely flexible platform on which to build
      decentralized applications using the native Solidity scripting language
      and Ethereum Virtual Machine. Decentralized application developers who
      deploy smart contracts on Ethereum benefit from the rich ecosystem of
      developer tooling and established best practices that have come with the
      maturity of the protocol. This maturity also extends into the quality of
      user-experience for the average user of Ethereum applications, with
      wallets like MetaMask, Argent, Rainbow and more offering simple interfaces
      through which to interact with the Ethereum blockchain and smart contracts
      deployed there. Ethereum’s large user base encourages developers to deploy
      their applications on the network, which further reinforces Ethereum as
      the primary home for decentralized applications like DeFi and NFTs. In the
      future, the backwards-compatible Ethereum 2.0 protocol, currently under
      development, will provide a more scalable network on which to build
      decentralized applications that require higher transaction throughput.
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
