<template>
  <div>
    <h1>Crypto WORLD</h1>
    <Input :changeAmount="changeAmount" :convert="convert" :favorite="favorite"/>      
    <div className="selectors">      
      <Selector :setCrypto="setCryptoFrom" :cryptoCurrency="cryptoFrom"/>
      <Selector :setCrypto="setCryptoTo"   :cryptoCurrency="cryptoTo"/>
    </div>
    <p className="error" v-if="error">{{ error }}</p>
    <p className="result" v-if="result != 0">{{ result }}</p>
    <Favorites :favs="favoriteCurrency" v-if="favoriteCurrency.length > 0" :getFromFavorites="getFromFavorites"/>  
  </div>
</template>

<script>
import Input from './components/Input.vue';
import Selector from './components/Selector.vue';
import Favorites from './components/Favorites.vue';
import CryptoConvert from 'crypto-convert';

const convert = new CryptoConvert();

export default {
  components: {
    Input,
    Selector,
    Favorites
  },
  data() {
    return {
      amount: 0,
      cryptoFrom: '',
      cryptoTo: '',
      error: '',
      result: 0,
      favoriteCurrency: []
    }
  },
  methods: {
    changeAmount(val) {
      this.amount = val
    },
    setCryptoFrom(val) {
      this.cryptoFrom = val
    },
    setCryptoTo(val) {
      this.cryptoTo = val
    },
    async convert() {
      if(this.amount <= 0) {
        this.error = 'Amount must be bigger than 0';
        return;
      } else if(!this.cryptoFrom || !this.cryptoTo) {
        this.error = 'Select crypto currency';
        return;
      } else if(this.cryptoFrom == this.cryptoTo) {
        this.error = 'Select different crypto currency';
        return;
      } 
      this.error = '';
      await convert.ready();
      this.result = convert[this.cryptoFrom][this.cryptoTo](this.amount);
    },
    favorite() {
      if(this.favoriteCurrency.length > 4) {
        this.error = 'Maximum 5 cryptocurrency pairs';
        return;
      }
      this.error = ''
      this.favoriteCurrency.push({
        from: this.cryptoFrom,
        to: this.cryptoTo
      })
    },
    getFromFavorites(index) {
      this.cryptoFrom = this.favoriteCurrency[index].from;
      this.cryptoTo = this.favoriteCurrency[index].to;
    }
  }
}
</script>

<style scoped>
.selectors {
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 3em auto;
}
.error {
  color: red;
  font-size: 1.2em;
  margin: 3em auto;
}
.result {
  margin: 3em auto;
  font-family: "Foldit", sans-serif;
  font-optical-sizing: auto;
  font-weight: bold;
  font-size: 4em;
  font-style: normal;    
  margin-top: 5rem;
}
</style>