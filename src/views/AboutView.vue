<template>
  <div class="about">
    <h1 class="header">More About This Marketplace</h1>
    <div class="introinfo">
      Welcome to Crypto Marketplace. This is not an exchange where you can
      trade, but rather a one stop website where you can find infromation about
      what cryptocurrency is and how it works. In this section you will find a
      synopsis of exactly what cryptocurrency is and some background on the
      technology used. Additionally there are some links on this page to some
      sources if you want to read more and gain a better understanding of
      Crypto, The Blockchain and how to start investing. And finally you will
      also find some links to digital exchanges if you want to dive right into
      trading crypto!
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
    <h1 class="header">Here Are Some Sources with More Information</h1>
    <h1 class="header">Below Are Links to Exchanges to Trade!</h1>
    <div class="all-exchanges">
      <div class="exchange-container">
        <a class="exchanges" href="https://crypto.com/" target="_blank"
          >Crypto.com
          <img src="https://i.imgur.com/urTkx5N.jpg" class="logo" />
        </a>
      </div>
      <div class="exchange-container">
        <a class="exchanges" href="https://www.gemini.com/" target="_blank"
          >Gemini
          <img src="https://i.imgur.com/iMbblss.png" class="logo" />
        </a>
      </div>
      <div class="exchange-container">
        <a class="exchanges" href="https://www.kraken.com/" target="_blank"
          >Kraken
          <img src="https://i.imgur.com/Fr6pIHf.png" class="logo" />
        </a>
      </div>
      <div class="exchange-container">
        <a class="exchanges" href="https://www.coinbase.com/" target="_blank"
          >Coinbase <img src="https://i.imgur.com/gv2B3BM.png" class="logo" />\
        </a>
      </div>
    </div>
    <!-- <ul class="item" v-for="item in list" :key="item.id">
      <li>{{ item.id }}</li>
      <li>{{ item.email }}</li>
      <li>{{ item.first_name }} {{ item.last_name }}</li>
      <li>
        <img :src="item.avatar" />
      </li>
    </ul> -->
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
  font-size: 18px;
}

@media only screen and (min-width: 500px) {
  .header {
    font-size: 24px;
  }
}

@media only screen and (min-width: 630px) {
  .header {
    font-size: 28px;
  }
}

@media only screen and (min-width: 768px) {
  .header {
    font-size: 35px;
  }
}

@media only screen and (min-width: 900px) {
  .header {
    font-size: 42px;
  }
}


.introinfo {
  width: 87.5%;
  margin-left: auto;
  margin-right: auto;
  font-size: 10px;
}

@media only screen and (min-width: 500px) {
  .introinfo {
    font-size: 14px;
  }
}

@media only screen and (min-width: 630px) {
  .introinfo {
    font-size: 18px;
  }
}

@media only screen and (min-width: 768px) {
  .introinfo {
    font-size: 22px;
  }
}

@media only screen and (min-width: 900px) {
  .introinfo {
    font-size: 27px;
  }
}

.all-exchanges {
  display: flex;
}

.exchange-container {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  width: 18%;
  transition: transform .2s;
  /* justify-content: center; */
}

.exchange-container:hover {
  transform: scale(1.15);
}

.exchanges {
  text-align: center;
  text-decoration: none !important;
  color: black;
  font-size: 12px;
}

@media only screen and (min-width: 550px) {
  .exchanges {
    font-size: 16px;
  }
}

@media only screen and (min-width: 768px) {
  .exchanges {
    font-size: 20px;
  }
}

@media only screen and (min-width: 900px) {
  .exchanges {
    font-size: 27px;
  }
}

.logo {
  /* width: 75%; */
  /* padding-left: 10%; */
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
