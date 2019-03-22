<template>
  <nuxt-link :to="'/blog/' + id">
    <div class="card">
      <div class="card-image">
        <figure class="image is-4by3">
          <img :src="thumbnailImage" alt="Thumbnail image">
        </figure>
      </div>
      <div class="card-content">
        <div class="content">
          <h1>{{title}}</h1>
          <p>{{text}}</p>
        </div>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    },
    thumbnailImage: {
      type: String,
      required: true
    },
    id: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
</style>