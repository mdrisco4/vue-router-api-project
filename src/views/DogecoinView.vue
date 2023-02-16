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
    <div class="title">Dogecoin</div>
    <div class="intro-information">
      Dogecoin (DOGE) is a peer-to-peer, open-source cryptocurrency. It is
      considered an altcoin and was launched in December 2013 with the image of
      a Shiba Inu dog as its logo. Dogecoin's blockchain has merit with its
      underlying technology derived from Litecoin. Notable features of Dogecoin,
      which uses a scrypt algorithm, are its low price and unlimited supply.
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
        this.cryptos = response.data.RAW.DOGE.USD;
        console.log(response.data);
        console.log(response.data.RAW.DOGE.USD);
        // console.log(this.cryptos)
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
