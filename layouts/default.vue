<template>
  <div class="site-canvas">
    <div id="header" class="absolute w-full">
      <div class="py-3 flex justify-between items-center container">
        <a href="/" class="no-underline flex items-center text-grey-darkest z-20">
          <span>Logo</span>
        </a>
        <navbar/>
      </div>
    </div>
    <Nuxt/>
  </div>
</template>

<script>
import Navbar from "~/components/Navbar.vue";

export default {
  components: {
    Navbar
  }
};
</script>

<style lang="css">
html {
  @apply font-normal;
  @apply text-black;
  @apply leading-normal;
  @apply font-copy;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  @apply font-heading;
  @apply text-black;
  @apply text-base;
}

p,
blockquote,
button,
a {
  @apply font-normal;
  @apply text-black;
  @apply text-base;
  @apply mb-3;
}

.object-cover {
  object-fit: cover;
}
</style>

<style lang="scss">
@import "~assets/scss/mixins";

.container {
  @apply px-8;
  @include mq(ns) {
    @apply px-16;
  }
  @extend %mwc;
}
</style>
