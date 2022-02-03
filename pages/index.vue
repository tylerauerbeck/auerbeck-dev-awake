<template>
  <div id="home-page" class="page-wrapper home-page">
    <site-hero :title="title" :subtitle="subtitle" :image="featureImage">
      <button
        v-if="$siteConfig.newsletter.on"
        class="button is-primary nav"
        @click="$eventBus.$emit('modal-triggered', 'newsletter-modal')"
      >
        Most Popular
      </button>
      <button
        v-if="$siteConfig.newsletter.on"
        class="button is-primary nav"
        @click="$eventBus.$emit('modal-triggered', 'newsletter-modal')"
      >
        Most Recent
      </button>
      <button
        v-if="$siteConfig.newsletter.on"
        class="button is-primary nav"
        @click="$eventBus.$emit('modal-triggered', 'newsletter-modal')"
      >
        Archives
      </button>
    </site-hero>
    <main-section theme="one-column">
      <!--<template v-slot:default> -->
        <!-- All Posts -->
      <!--  <posts-grid /> -->
      <!--</template> -->

      <template v-slot:default>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <posts-grid :per-row="3" :number="2" />
      </template>



      <template v-slot:sidebar>
        Nothing here
      </template>
    </main-section>
    <news-letter-form-modal />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import { setPageData } from '../helper'
import NewsLetterFormModal from '~/components/NewsLetterFormModal'

export default {
  name: 'HomePage',
  head() {
    return {
      title: `Home | ${this.$siteConfig.siteName}`
    }
  },
  components: {
    NewsLetterFormModal
  },
  computed: {
    ...mapState(['title', 'subtitle', 'featureImage'])
  },
  fetch({ store, params }) {
    setPageData(store, { slug: 'home' })
  }
}
</script>

<style>
.home-page .under-subtitle {
  border-top: none;
}

.button.nav {
  padding: 1.0625rem 2.25rem;
  margin: 0 .875rem 0 0;
}
</style>
