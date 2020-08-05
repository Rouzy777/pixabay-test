<template>
  <div class="container-fluid pt-5">
    <input v-model="searchLine" @keyup.enter="searchCall" ref="searchLine" placeholder="Search images" class="form-control">
    <div v-if="Array.isArray(hits) && hits.length" class="card-columns mt-3">
      <Post v-for="i of hits" :key="i.pageURL" :data="i" />
    </div>
    <div v-else-if="Array.isArray(hits) && !hits.length" class="text-center">
      <h3 class="text-muted font-weight-light mt-5">Nothing was found</h3>
    </div>
    <div v-else class="text-center">
      <h3 class="text-muted font-weight-light mt-5">Write anything and press enter...</h3>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Post from '@/components/Post'

export default {
  name: 'App',
  components: {
    Post
  },
  data: () => ({
    searchLine: '',
    hits: null
  }),
  mounted () {
    this.$refs.searchLine.focus() // focus on input when mounted
  },
  methods: {
    async searchCall () {
      const filteredSearchLine = this.searchLine.replace(/ /g, '+')
      const response = await axios.get(
        `https://pixabay.com/api/?key=17779624-c7b9998197af18a5bd96c56cc&q=${filteredSearchLine}`
      )

      this.hits = response.data.hits
    }
  }
}
</script>
