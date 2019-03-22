<template>
  <div class="header">
    <header>
      <nuxt-link class="logo" to="/">
        <h1 class="title is-4">Storyblok</h1>
      </nuxt-link>
      <ul class="my-navbar-menu">
        <li class="item">
          <nuxt-link class="link" to="/blog">All Posts</nuxt-link>
        </li>
        <li class="item">
          <nuxt-link class="link" to="/about">About</nuxt-link>
        </li>
      </ul>
    </header>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.header {
  background: var(--nav-bg);
  header {
    height: 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    color: var(--nav-color);
    width: 100%;
    max-width: 1280px;
    margin: 0 auto;
    .logo h1 {
      color: var(--font-light);
      opacity: 1;
    }
    .my-navbar-menu {
      margin: 0;
      padding: 0;
      list-style: none;
      display: flex;
      .item {
        position: relative;
        text-align: center;
        transition-duration: 0.3s;
        .link {
          position: relative;
          color: var(--nav-color);
          font-size: 1.1rem;
          display: inline-block;
          padding: 1.1rem;
          cursor: pointer;
          transition-duration: 0.1s;
          &:after {
            content: "";
            background-color: var(--nav-active-color);
            transform: scaleY(0);
            transform-origin: bottom;
            position: absolute;
            bottom: 1px;
            left: 0;
            height: 4px;
            width: 100%;
            transition: transform 0.3s;
          }
          &:hover,
          &.nuxt-link-active {
            color: var(--nav-active-color);
            &:after {
              transform: scaleY(1);
            }
          }
        }
      }
    }
  }
}
</style>
