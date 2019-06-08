<template>
  <section>
    <div>
      <main-header></main-header>
    </div>
    <filler></filler>
    <filler></filler>
    <filler></filler>
    <filler></filler>
    <filler></filler>

  </section>
</template>

<script>
import Logo from "~/components/Logo.vue";
import IconLink from "~/components/IconLink.vue";
import MainHeader from "~/components/MainHeader.vue";
import Filler from "~/components/Filler.vue";

export default {
  components: {
    Logo,
    IconLink,
    MainHeader,
    Filler
  }
};
</script>

<style scoped>
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 400;
  font-size: 100px;
  color: #2E495E;
  letter-spacing: 1px;
  font-size: 6em;
}
.green {
  color: #00C48D;
}

.subtitle {
  font-weight: 300;
  font-size: 3em;
  color: #2E495E;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
