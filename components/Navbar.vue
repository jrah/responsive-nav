<template>
  <nav v-if="document_data" :class="{ isOpen: isOpen }" class="nav flex items-center justify-end">
    <ul class="hidden list-reset ns:flex flex-wrap justify-between items-center z-20 relative">
      <!-- <a href="#" class="absolute pin-t pin-l">View Policies</a> -->
      <li
        v-for="(linkGroup, i) in document_data.body"
        :key="i"
        class="dib ns:mr-4 l:mr-6 flex-auto"
      >
        <nuxt-link
          class="primary-link text-white no-underline mb-4 text-lg pb-1 border-transparent border-b-2 hover:border-blue"
          :to="`/${linkGroup.primary.nav_link.uid}`"
        >{{ linkGroup.primary.link_text }}</nuxt-link>

        <ul class="hidden list-reset z-20 relative my-4">
          <li v-for="(link, k) in linkGroup.items" :key="k" class="dib mb-1">
            <nuxt-link
              v-if="link.third_level_link.uid"
              class="secondary-link text-white hover:text-blue no-underline text-lg"
              :to="link.third_level_link.uid"
            >{{ link.third_level_link_text }}</nuxt-link>
            <a
              v-else
              :href="link.third_level_link.url"
              class="secondary-link text-white hover:text-blue no-underline text-lg"
            >{{ link.third_level_link_text }}</a>
          </li>
        </ul>
        <!-- -->
      </li>
    </ul>
    <div
      v-if="isOpen"
      :class="{ isOpenToggleOpen: isOpen }"
      class="cursor-pointer absolute pin-y pin-r p-4"
      @click="toggleNav()"
    >
      <font-awesome-icon icon="times" size="2x" color="black"/>
    </div>
    <div
      v-else
      :class="{ isOpenToggleOpen: isOpen }"
      class="cursor-pointer relative z-20"
      @click="toggleNav()"
    >
      <font-awesome-icon icon="bars" size="2x" color="white"/>
    </div>
  </nav>
</template>

<script>
import document_data from "~/content.json";
export default {
  data() {
    return {
      isOpen: false,
      document_data
    };
  },
  methods: {
    closeNav() {},
    toggleNav() {
      this.isOpen = !this.isOpen;
      // eslint-disable-next-line no-unused-vars
      const header = document.querySelector("#header");
      const site = document.querySelector(".site");
      site.classList.toggle("position-fixed");
      // eslint-disable-next-line no-console
      // console.log(header);

      // if (site.contains('position-fixed')) {
      //   document.querySelector('#header').classList.remove('position-fixed')
      // } else {
      //   document.querySelector('#header').classList.add('position-fixed')
      // }
      // document.querySelector('header').classList.toggle('h-screen')
    }
  }
};
</script>

<style lang="scss">
@import "assets/scss/mixins";

// .isOpen {
//   display: block;
//   position: absolute;
//   top: 0;
//   bottom: 0;
//   left: 0;
//   right: 0;
//   width: 100%;
//   z-index: 40;
//   height: 100vh;
//   @apply bg-white;
//   &Toggle {
//     padding-right: 4rem;
//     max-width: 72em;
//   }
// }

.position-fixed {
  height: 100%;
  position: relative;
  overflow: hidden;
  @apply bg-white;
}

.nav--fixed {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.nav {
  transition: background-color 0.5s ease;
  @apply bg-transparent;
}

.isOpen {
  position: absolute;
  height: 100vh;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  @apply bg-white;
  @apply text-black;
  z-index: 50;
  justify-content: center;
  @apply p-4;
  &ToggleOpen {
    // display: none;
  }
  &ToggleClose {
    display: block;
  }
  ul {
    display: flex;
    .primary-link {
      @apply text-black;
      @apply border-0;
      @apply text-2xl;
    }
    a {
      @apply text-blue;
    }
    ul {
      display: block;
    }
  }
}

// .pin-important {
//   position: absolute;
//   top: 1.5em;
// }
</style>
