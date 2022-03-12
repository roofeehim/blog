<template>
  <div>
    <Header></Header>
    <ul>
      <li v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData() {
    const { data } = await axios.get(
      'https://62hwvp7q8d.microcms.io/api/v1/blog',
      {
        headers: { 'X-MICROCMS-API-KEY': '945706f044414f119a5a66a6a0cdbe68f55c' }
      }
    )
    return data
  }
}
</script>

<style scoped>
ul{
  list-style: none;
}
li{
  margin: 10px 0 0 0;
  font-size: 18px;
}
a{
  text-decoration: none;
}
</style>