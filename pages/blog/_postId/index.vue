<template>
  <div class="my-container">
    <div class="post-detail-wrapper" v-editable="edit">
      <div class="image" :style="{backgroundImage: 'url(' + image +')'}"></div>
      <section class="post-content content">
        <nuxt-link to="/blog" class="button is-primary">Back to posts</nuxt-link>
        <h1>{{title}}</h1>
        <p>{{content}}</p>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  asyncData(context) {
    return context.app.$storyapi
      .get("cdn/stories/blog/" + context.params.postId, {
        version: process.env.NODE_ENV == "production" ? "published" : "draft"
      })
      .then(res => {
        console.log(res.data);
        const { title, thumbnail: image, content } = res.data.story.content;
        return {
          edit: res.data.story.content,
          title,
          image,
          content
        };
      })
      .catch(res => {
        if (!res.response) {
          console.error(res);
          context.error({
            statusCode: 404,
            message: "failed to receive content from api"
          });
        } else {
          console.error(res.response.data);
          context.error({
            statusCode: res.response.status,
            message: res.response.data
          });
        }
      });
  }
};
</script>

<style scoped lang="scss">
.post-detail-wrapper {
  width: 100%;
  max-width: 1000px;
  margin: 0 auto;
  .image {
    width: 100%;
    height: 300px;
    background-size: cover;
    background-position: center;
  }
  .post-content {
    padding: 2rem;
    p {
      white-space: pre-line;
    }
  }
}
</style>