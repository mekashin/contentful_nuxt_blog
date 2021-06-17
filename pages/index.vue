<template>
  <div>
    <Header />
     <link href="~assets/style_00.css" type="text/css" media="all">

    <p>{{ posts }}</p>
    <p class="img"><img src="~assets/objctsio_pic2.png"></p>
    <section class="index">
      <card
        v-for="(post, i) in posts"
        :key="i"
        :title="post.fields.title"
        :id="post.sys.id"
        :date="post.sys.updatedAt"
        :post='post'
        :key_id='i'
      />
    </section>
    <Footer />
  </div>
</template>

<script>
// export default {};
import Card from "~/components/card.vue";
import { createClient } from "~/plugins/contentful.js";
// export default {
//   components: {
//     Card
//   }
// };
const client = createClient();
export default {
  transition: "slide-left",
  components: {
    Card
  },
  asyncData({ env, params }) {
    return client
      .getEntries(env.CTF_BLOG_POST_TYPE_ID)
      .then(entries => {
        return {
          posts: entries.items
        };
      })
      .catch(console.error);
  }
};
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
