<template>
  <div>
    <Header></Header>
    <main class="main">
      <h2 class="title">{{ title }}</h2>
      <p class="publishedAt"><time :datetime="publishedAt" v-text="$dateFns.format(new Date(publishedAt), 'yyyy.MM.dd')"
        /></p>
      <h5>{{ category && category.name }}</h5>
      <div class="post" v-html="body"></div>
    </main>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://62hwvp7q8d.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-MICROCMS-API-KEY': '945706f044414f119a5a66a6a0cdbe68f55c' }
      }
    )
    return data
  }
}
</script>