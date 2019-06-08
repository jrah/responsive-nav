<template>
  <div v-if="document_data" class="nav-wrapper" :class="{ isNavOpen: isOpen, lightThemeNav: isOpen }">
    <nav 
      class="nav flex items-center justify-end" 
      :class="{container: isOpen}"
    >
      <ul class="list-reset ns:flex flex-wrap justify-between items-center z-20 relative">
        <!-- <a href="#" class="absolute pin-t pin-l">View Policies</a> -->
        <li
          v-for="(linkGroup, i) in document_data.body"
          :key="i"
          class="dib ns:mr-4 l:mr-6 flex-auto"
        >
          <nuxt-link
            class="primary-link text-white no-underline mb-4 text-lg pb-1 border-transparent border-b-2 hover:border-blue"
            :to="`/${linkGroup.primary.nav_link.uid}`"
          >
            {{ linkGroup.primary.link_text }}
          </nuxt-link>

          <ul class="hidden list-reset z-20 relative my-4">
            <li v-for="(link, k) in linkGroup.items" :key="k" class="dib mb-1">
              <nuxt-link
                v-if="link.third_level_link.uid"
                class="secondary-link text-white hover:text-blue no-underline text-lg"
                :to="link.third_level_link.uid"
              >
                {{ link.third_level_link_text }}
              </nuxt-link>
              <a
                v-else
                :href="link.third_level_link.url"
                class="secondary-link text-white hover:text-blue no-underline text-lg"
              >
                {{ link.third_level_link_text }}
              </a>
            </li>
          </ul>
        </li>
      </ul>
      <!-- Navbar Toggle button -->
      <div
        class="cursor-pointer relative z-20"
        @click="toggleNav()"
        :aria-expanded="ariaExpandedText"
        aria-label="Toggle Navigation"
      >
        <font-awesome-icon :icon="fontAwesomeIcon" :color="fontAwesomeIconColor" size="2x" />
      </div>
    </nav>
  </div>
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
  computed: {
    fontAwesomeIcon() {
      return this.isOpen ? 'times' : 'bars';
    },
    fontAwesomeIconColor() {
      return this.isOpen ? 'black' : 'white';
    },
    ariaExpandedText() {
      return this.isOpen ? 'true' : 'false';
    }
  },
  methods: {
    closeNav() {},
    toggleNav() {
      this.isOpen = !this.isOpen;
    }
  }
};
</script>

<style lang="scss">
@import "assets/scss/mixins";

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

.nav-wrapper {
  transition: background-color 0.3s linear;
}

.isNavOpen {
  @apply bg-white;
  @apply p-4;
  @apply text-black;
  align-items: flex-start;
  height: 100vh;
  justify-content: center;
  left: 0;
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 50;
  ul {
    display: flex;
    align-items: flex-start;
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
  & > .nav {
    align-items: flex-start;
  }
}

// .pin-important {
//   position: absolute;
//   top: 1.5em;
// }
</style>
