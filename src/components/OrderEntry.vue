<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="entrySecret" id="entrySecret" name="entrySecret" placeholder="Enter password..." style="margin-left:40px;width:400px;">
    <br/>
    <p>Percentage</p>
    <label class="container">25    <input type="radio" v-model="buyPercentage" value="25" name="radioBuy"><span class="checkmark"></span></label>
    <label class="container">50    <input type="radio" v-model="buyPercentage" value="50" name="radioBuy"><span class="checkmark"></span></label>
    <label class="container">75    <input type="radio" v-model="buyPercentage" value="75" name="radioBuy"><span class="checkmark"></span></label>
    <label class="container">90    <input type="radio" v-model="buyPercentage" value="90" checked="checked" name="radioBuy"><span class="checkmark"></span></label>
    <label class="container">100<input type="radio" v-model="buyPercentage" value="100" name="radioBuy"><span class="checkmark"></span></label>
    <br/>
    <br/>
    <label for="symbol">Symbol to buy with BTC</label>
    <br/>
    <input type="text" v-model="buySymbol" id="buySymbol" name="buySymbol" placeholder="Enter symbol..." v-on:keyup.enter="enterBuy">

    <input type="submitBuy" v-on:click="enterBuy" value=" BUY BUY BUY BUY BUY">

    <br/>
    <br/>
    <br/>

    <p> Percentage </p>
    <label class="container">25    <input type="radio" checked="checked" v-model="sellPercentage" value="25" name="radioSell"><span class="checkmark"></span></label>
    <label class="container">50    <input type="radio" v-model="sellPercentage" value="50" name="radioSell"><span class="checkmark"></span></label>
    <label class="container">75    <input type="radio" v-model="sellPercentage" value="75" name="radioSell"><span class="checkmark"></span></label>
    <label class="container">90    <input type="radio" v-model="sellPercentage" value="90" name="radioSell"><span class="checkmark"></span></label>
    <label class="container">100<input type="radio" v-model="sellPercentage" value="100" name="radioSell"><span class="checkmark"></span></label>
    <br/>
    <br/>
    <label for="symbol">Symbol to sell for BTC</label>
    <br/>
    <input type="text" v-model="sellSymbol" id="sellSymbol" name="sellSymbol" placeholder="Enter symbol..." v-on:keyup.enter="enterSell">

    <input type="submitSell" v-on:click="enterSell" value=" SELL AHHHHHHHHHHHHH">
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'OrderEntry',
  props: {
    msg: String,
  },
  data() {
    return {
      buySymbol: '',
      buyPercentage: '',
      sellSymbol: '',
      sellPercentage: '',
      entrySecret: '',
    }
  },
  methods: {
    async enterBuy() {
      const buyUrl = `http://localhost:3000/orders/buy?symbol=${this.buySymbol}&percentage=${this.buyPercentage}&secretPhrase=${this.entrySecret}`;
      // eslint-disable-next-line
      console.log(`Req: ${buyUrl}`);
      await axios.get(buyUrl).then(res => {
        if (res.status === 200) {
          // eslint-disable-next-line
          console.log("Buy Order entered.");
        }
      })
      .catch(e => {
        // eslint-disable-next-line
        console.log(e);
      })
    },
    async enterSell() {
      const sellUrl = `http://localhost:3000/orders/sell?symbol=${this.sellSymbol}&percentage=${this.sellPercentage}&secretPhrase=${this.entrySecret}`;
      // eslint-disable-next-line
      console.log(`Req: ${sellUrl}`);
      await axios.get(sellUrl).then(res => {
        if (res.status === 200) {
          // eslint-disable-next-line
          console.log("Sell Order entered.");
        }
      })
      .catch(e => {
        // eslint-disable-next-line
        console.log(e);
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
/* Customize the label (the container) */
.container {
  align-content: center;
  display: inline;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default radio button */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom radio button */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #eee;
  border-radius: 50%;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the radio button is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #c7ab50;
}

/* Create the indicator (the dot/circle - hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the indicator (dot/circle) when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the indicator (dot/circle) */
.container .checkmark:after {
  top: 9px;
  left: 9px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: white;
}

input[type=text], select, textarea {
  width: 200px;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  margin-right: 20px;
  resize: vertical;
}

input[type=submitBuy] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submitSell] {
  background-color: rgb(255, 0, 0);
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
</style>
