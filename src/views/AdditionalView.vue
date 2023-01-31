<template>
  <div class="additional">
      <div id="column-titles">
          <div class="left">Coin</div>
          <div class="middle-left">Daily Low</div>
          <div class="middle-right">Daily High</div>
          <div class="right">Current</div>
        </div>
    <div
      id="crypto-container"
      v-for="(item, index) in cryptos"
      v-bind:key="index"
    >
        <div class="left">{{ item.USD.FROMSYMBOL }}</div>
        <div class="middle-left">{{ item.USD.LOWDAY }}</div>
        <div class="middle-right">{{ item.USD.HIGHDAY }}</div>
        <div class="right">${{ item.USD.PRICE }}</div>
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

div#crypto-container {
    background-color: white;
    width: 70%;
    margin: 0 auto 4px auto;
    padding: 1em;
    box-shadow: 1px 1px 0 lightgray;
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

@media only screen and (min-width: 1100px) {
  div.left {
    
  }
}

@media only screen and (min-width: 1100px) {
  div.left {
    
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

@media only screen and (min-width: 1100px) {
    div.middle-left {
    
  }
}

@media only screen and (min-width: 1100px) {
    div.middle-left {
    
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

@media only screen and (min-width: 1100px) {
    div.middle-right {
    
  }
}

@media only screen and (min-width: 1100px) {
    div.middle-right {
    
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

@media only screen and (min-width: 1100px) {
    div.right {
    
  }
}

@media only screen and (min-width: 1100px) {
    div.right {
    
  }
}

</style>
