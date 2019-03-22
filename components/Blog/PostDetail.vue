<template>
  <div class="card">
    <div class="card-image">
      <figure class="image is-4by1">
        <img :src="image" alt="Thumbnail image">
      </figure>
    </div>
    <div class="card-content">
      <div class="content">
        <h1>{{title}}</h1>
        <p>{{content}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    content: {
      type: String,
      required: true
    },
    image: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
</style>