<template>
  <div>
    <input v-model="query" class="inputs" style="height:70px; width:500px">
    <button @click="getData" style="height:73px; width:100px">ПОИСК</button>
    <div id="app" style="font-size:25px; line-height:45px">
        Адрес: {{ addres }} </br>
        Тип отделения: {{ type }} </br>
        Почтовый индекс: {{ index }} </br>
        Широта: {{ lat }} </br>
        Долгота: {{ lon }}
    </div>
  </div>
</template>
<script>
const axios = require('axios');

export default {
  data() {
    return {
      addres: null,
      type: null,
      index: null,
      lat: null,
      lon: null,
      query: null,
      newStr: null,
    };
  },
methods: {
    async getData() {
    axios
        .post('https://suggestions.dadata.ru/suggestions/api/4_1/rs/suggest/postal_unit', { query: this.query }, { headers: {"Content-Type": "application/json",
    "Authorization": process.env.API_KEY,
    "Accept": "application/json",
    "Cache-Control": "no-cache",
    "Postman-Token": "637d415d-34eb-40ab-8655-e78a192a71d1,b82d0f9a-7660-4b36-8b95-cf89b225a567",
    "cache-control": "no-cache"}})
        .then((response => (this.addres = JSON.stringify(response.data.suggestions[0].data.address_str), this.type = JSON.stringify(response.data.suggestions[0].data.type_code), this.index = JSON.stringify(response.data.suggestions[0].data.postal_code), this.lat = JSON.stringify(response.data.suggestions[0].data.geo_lat), this.lon = JSON.stringify(response.data.suggestions[0].data.geo_lon))));
  }
},
  
}
</script>



