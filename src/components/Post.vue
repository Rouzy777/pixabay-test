<template>
  <div class="card px-0">
    <a :href="data.pageURL">
      <img class="card-img-top" :src="data.webformatURL" alt="Image">
    </a>
    <div class="card-body row py-2 text-muted">
      <div class="col-lg-6">
        <small>🏷️ {{ data.tags }}</small>
      </div>
      <div class="col-lg-6 text-lg-right">
        <small>id: {{ data.id }}</small>
      </div>
    </div>
    <div class="card-footer row mx-0 px-0 py-2">
      <div class="col-lg-6">
        <small>&#128100; {{ data.user }}</small>
      </div>
      <div class="col-lg-6 text-lg-right">
        <small>❤️ {{ data.likes }}</small>
        <small class="mx-1"> ⭐ {{ data.favorites }}</small>
        <small> 💭 {{ data.comments }}</small>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Post',
  props: {
    data: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="css" scoped>
</style>
