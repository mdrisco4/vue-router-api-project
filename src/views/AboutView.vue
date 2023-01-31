<template>
  <div class="about">
    <h1 class="header">More About This Marketplace</h1>
    <div class="introinfo">
      Welcome to Crypto Marketplace. This is not an ex change but rather a one
      stop website where you can find infromation about what cryptocurrency is
      and how it works. Additionally there are some links on this page to good
      sources if you want to read more and gain a better understanding of
      Crypto, The Blockchain and how to start investing.
    </div>
    <div class="introinfo">
      Cryptocurrency is a decentralized monetary platform fueled by a technology
      called Blockchain. The Blockchain is a way of recording information that
      makes it impossible to cheat the system. This allows for secure exchanges
      of digital currencies across decentralized exchanges. Every time a
      tranaction is conducted a record of that transaction is added to the
      participant's ledger. The digital currencies being traded among
      individuals, financial institutions and others are kept in Crypto Wallets.
    </div>
    <div class="introinfo">
      Crypto Wallets securely store your personal private keys, which are
      required for access to the blockachain and therefore in order to retrieve
      and trade your funds. There are 2 different types of wallets that can be
      used, hot and cold. Hot wallets remain connected to the internet and
      include custodial and non-custodial wallets.
    </div>
    <div class="introinfo">
      Custodial wallets require you to maintain and have access to your own
      private keys, while custodial wallets entrust that responsibility to a
      third party. The most common typr of custodial wallets are the kind that
      you might use on popular exchanges like Crypto.com and Gemini. We will
      touch more on that briefly.
    </div>
    <div class="introinfo">
      Cold wallets on the other hand are entirely maintained by the users of the
      wallets themselves. This is to say that the owners of those wallets must
      maintain and retain access to the keys to those wallets. If they lose
      those keys and are unable to retrieve them for any reason the funds
      contained are lost forever, this is called burning crypto and is sometimes
      done to increase the value of the ramining crypto of that type. The upside
      of using a cold wallet is that it generally remains much more secure. One
      way in which these types of wallets are kept is on an external or
      removeable harddrive. By not remaining connected to the internet AND
      having the advantage to be kept in any secure, physical location wallets
      of this type can be safely kept by users more easily.
    </div>
    <h1 class="header">
      Here Are Some Sources with Additional Information
    </h1>
    <h1 class="header">
      Below Are Links to Exchanges to Start Trading!
    </h1>
    <div class="all-exchanges">
    <div class="exchange-container">
      <a class="exchanges" href="https://crypto.com/" target="_blank">Crypto.com</a>
      <img src="https://i.imgur.com/urTkx5N.jpg" class="logo" />\
    </div>
    <div class="exchange-container">
      <a class="exchanges" href="https://www.gemini.com/" target="_blank">Gemini</a>
      <img src="https://i.imgur.com/iMbblss.png" class="logo" />\
    </div>
    <div class="exchange-container">
      <a class="exchanges" href="https://www.kraken.com/" target="_blank">Kraken</a>
      <img src="https://i.imgur.com/aHYfhWi.png" class="logo" />\
    </div>
    <div class="exchange-container">
      <a class="exchanges" href="https://www.coinbase.com/" target="_blank">Coinbase</a>
      <img src="https://i.imgur.com/gv2B3BM.png" class="logo" />\
    </div>
  </div>
    <ul class="item" v-for="item in list" :key="item.id">
      <li>{{ item.id }}</li>
      <li>{{ item.email }}</li>
      <li>{{ item.first_name }} {{ item.last_name }}</li>
      <li>
        <img :src="item.avatar" />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HomeView",
  data() {
    return {
      list: [],
    };
  },

  async mounted() {
    let result = await axios.get("https://reqres.in/api/users?page=1");
    console.log(result.data.data);
    this.list = result.data.data;
  },
};
</script>

<style>
.header {
  text-align: center;
  text-decoration: underline;
}

.introinfo {
  width: 87.5%;
  margin-left: auto;
  margin-right: auto;
}

.all-exchanges {
  display: flex;
}

.exchange-container {
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
}

.exchanges {
  text-align: center;
}

.logo {
  width: 75%;
  padding-left: 12.5%;
  /* justify-content: center; */
}

.item {
  display: flex;
  justify-content: center;
}

@media only screen and (min-width: 600px) {
  .item {
    background-color: green;
  }
}

.item li {
  display: inline-block;
  border: 1px solid black;
  width: 180px;
  text-align: center;
  padding: 5px;
}

@media only screen and (min-width: 600px) {
  .item li {
    background-color: yellow;
  }
}

.item img {
  width: 50px;
}

@media only screen and (min-width: 600px) {
  .item img {
    background-color: lightblue;
  }
}
</style>
