<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        sample_01_test02
      </h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
    <!-- <section class="index">
      <p>card</p>
      <card v-for="i in 5" :key="i" />
    </section> -->
    <section class="index">
      <card
        v-for="(post, i) in posts"
        :key="i"
        :title="post.fields.title"
        :id="post.sys.id"
        :date="post.sys.updatedAt"
      />
    </section>
  </div>
</template>

<script>
// export default {};
import Card from '~/components/card.vue'
import { createClient } from '~/plugins/contentful.js'
// export default {
//   components: {
//     Card
//   }
// };
const client = createClient()
export default {
  transition: 'slide-left',
  components: {
    Card
  },
  asyncData({ env, params }) {
    return client
      .getEntries(env.CTF_BLOG_POST_TYPE_ID)
      .then(entries => {
        return {
          posts: entries.items
        }
      })
      .catch(console.error)
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
