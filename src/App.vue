<script setup>

</script>

<template>
  <div>Hello</div>

  <button @click="fetchData"> CLICK HERE</button>

  <div v-if="show"> SELAM </div>

  <div v-if="show"> {{ result[0].Açıklama }} </div>

  <input type="text" :value="val" @input="display">

</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      result: null,
      show: false,
      val: "asdasd"
    }
  },
  methods: {
    async fetchData() {
      let data = JSON.stringify({
        "productCode": "TR7-v7005-U-WAF-0Y",
        "type": "PRODUCT",
        "platform": "Virtual Image",
        "quantity": "ClusterUpgrade",
        "licenseTime": "-",
        "edition": "WAF",
        "properties": "WAF"
      });

      let config = {
        method: 'post',
        maxBodyLength: Infinity,
        url: 'http://localhost:3000/search',
        headers: {
          'Content-Type': 'application/json'
        },
        data : data
      };

      axios.request(config)
          .then((response) => {
            this.result = response.data
            this.show = true
          })
          .catch((error) => {
            console.log(error);
          });
    },
    display() {
      console.log("hi")
    }
  }
}
</script>
