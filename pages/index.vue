<template>
  <div>
    <input class="inputs" style="height:70px; width:500px">
  </div>
</template>
<script>
var url = "https://cleaner.dadata.ru/api/v1/clean/address";
var token = "37ea5e15a9c61b401af9b23bee9563ef7654f126";
var secret = "26ed63e476256db8bf5e7ffa390107ff681f7860";
var query = "мск сухонска 11/-89";
var options = {
    method: "POST",
    mode: "cors",
    headers: {
        "Content-Type": "application/json",
        "Authorization": "Token " + token,
        "X-Secret": secret
    },
    body: JSON.stringify([query])
}
export default {
  async asyncData({ $axios }) {
    const mountains = await $axios.$get('https://cleaner.dadata.ru/api/v1/clean/address', options, query)
    return { mountains }
  }
}
</script>



