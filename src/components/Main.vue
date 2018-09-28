<template>
  <div id="faucetDiv">
    <div id="title">FUSORA FAUCET</div>
    <div/> 
    <div> Address :</div>
		<input class="input" v-model="address" placeholder="Private Key">
    <div />
    <button class="button" v-on:click="callFaucet()"> Load Key </button>
    <simplert id="alert" useRadius="true" :useIcon="true" ref="simplert">
    </simplert>
  </div>
</template>

<script>
import axios from "axios";
import Simplert from "vue2-simplert";
import 'vue2-simplert/dist/simplert.common.css';
export default {
  data: function() {
    return {
      address: ""
    };
  },
  methods: {
    callFaucet
  },
  components: { Simplert }
};

function callFaucet() {
  console.log(this.address)
  axios
    .get(`https://fusora-faucet.herokuapp.com/request/${this.address}`)
    .then(res => {
      console.log(res);
      let obj = {
        title: "Requested",
        message: "Wait for the transaction to be mine",
        type: "success"
      };
      this.$refs.simplert.openSimplert(obj);
    })
    .catch(err => {
      console.log(err)
      let obj = {
        title: "Greedy User",
        message: "Greedy User or Dry Faucet",
        type: "error"
      };
      this.$refs.simplert.openSimplert(obj);
    });
}
</script>
<style scoped>
#title {
  font-size: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 20px;
}

#faucetDiv {
  color: white;
  font-size: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 20px;
}

.button {
  margin: 15px;
  border-radius: 10px;
  padding: 12px 28px;
  background-color: #000060;
  border-color: #005de0;
  color: #e0ffff;
  font-family: "Lato", sans-serif;
  font-size: 15px;
}

.input {
  width: 700px;
  height: 30px;
  border-radius: 5px;
  margin: 10px;
}

#alert {
  color: black;
}
</style>
