<template>
  <div>
    <input v-model="query" class="inputs" style="height:70px; width:500px">
    <button @click="getData" style="height:73px; width:100px">ПОИСК</button>
    <div id="app">
        {{ res }}
    </div>
  </div>
</template>
<script>
const axios = require('axios');

export default {
  data() {
    return {
      res: null,
      query: null
    };
  },
methods: {
    async getData() {
    axios
        .post('https://suggestions.dadata.ru/suggestions/api/4_1/rs/suggest/postal_unit', { query: this.query }, { headers: {"Content-Type": "application/json",
    "Authorization": "Token 37ea5e15a9c61b401af9b23bee9563ef7654f126",
    "Accept": "application/json",
    "Cache-Control": "no-cache",
    "Postman-Token": "637d415d-34eb-40ab-8655-e78a192a71d1,b82d0f9a-7660-4b36-8b95-cf89b225a567",
    "cache-control": "no-cache"}})
        .then(response => (this.res = response.data.suggestions));
  }
},
  
}
</script>



