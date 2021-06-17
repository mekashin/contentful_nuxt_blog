<template>
  <div class="wrap-all">
    <div id="wrap-outer">
      <Header />
      <div id="wrap" class=" typesquare_option typesquare_option">
        <main class="frontpage typesquare_option typesquare_option">
          <div class="frontpage-fv">
            <div class="_spNone">
              <img src="~assets/index/fv_bg2.png" alt="" class="js-randomImg" />
            </div>
            <div class="_spOnly">
              <img src="~assets/index/fv_bg1_sp.png" alt="" />
            </div>
          </div>
          <div class="inner typesquare_option">
            <h2 class="frontpage-tit typesquare_option">
              Total Branding Partner FRACTA<br />ブランドを、未来の文化へ。
            </h2>
          </div>
                 <section class="frontpage-news typesquare_option">
            <div class="inner typesquare_option">
              <h2
                class="frontpage-news-tit js-tpnews t_js typesquare_option"
                data-chaffle="en"
                style="opacity: 1; position: relative; overflow: hidden; visibility: visible;"
              >
                <span class="t-container" style="top:auto;bottom:auto;"
                  >Works</span
                ><span class="t-caret" style="visibility: hidden; opacity: 0;"
                  >▎</span
                >​
              </h2>
              <div class="frontpage-news-content typesquare_option">
                <ul class="newsList typesquare_option">
                  <news_card
                    v-for="(post, i) in works_ary"
                    :key="i"
                    :category="post.fields.category"
                    :title="post.fields.title"
                    :thumbnail="post.fields"
                    :id="post.sys.id"
                    :date="post.sys.updatedAt"
                    :post="post"
                    :key_id="post.key_id"
                    :update="post.fields.date"
                  />
                </ul>
                <div class="frontpage-news-btn typesquare_option">
                  <nuxt-link
                    to="/list/works"
                    class="btn _more typesquare_option"
                  >
                    <span class=" typesquare_option">Works</span>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="50.74"
                      height="41.957"
                      viewBox="0 0 50.74 41.957"
                    >
                      <g transform="translate(-297.5 -1435.771)">
                        <path
                          data-name="パス 186"
                          d="M-3567.73,1909l20.625,20.625-20.625,20.625"
                          transform="translate(3894.639 -472.875)"
                          fill="none"
                          stroke="#767676"
                          stroke-width="1"
                        ></path>
                        <line
                          data-name="線 1"
                          x1="50.224"
                          transform="translate(297.5 1457.125)"
                          fill="none"
                          stroke="#707070"
                          stroke-width="1"
                        ></line>
                      </g>
                    </svg>
                  </nuxt-link>
                </div>
              </div>
            </div>
          </section>
          <section class="frontpage-news typesquare_option">
            <div class="inner typesquare_option">
              <h2
                class="frontpage-news-tit js-tpnews t_js typesquare_option"
                data-chaffle="en"
                style="opacity: 1; position: relative; overflow: hidden; visibility: visible;"
              >
                <span class="t-container" style="top:auto;bottom:auto;"
                  >News​</span
                ><span class="t-caret" style="visibility: hidden; opacity: 0;"
                  >▎</span
                >​
              </h2>
              <div class="frontpage-news-content typesquare_option">
                <ul class="newsList typesquare_option">
                  <news_card
                    v-for="(post, i) in news_ary"
                    :key="i"
                    :category="post.fields.category"
                    :title="post.fields.title"
                    :thumbnail="post.fields"
                    :id="post.sys.id"
                    :date="post.sys.updatedAt"
                    :post="post"
                    :key_id="post.key_id"
                    :update="post.fields.date"
                  />
                </ul>
                <div class="frontpage-news-btn typesquare_option">
                  <nuxt-link
                    to="/list/news"
                    class="btn _more typesquare_option"
                  >
                    <span class=" typesquare_option">News</span>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="50.74"
                      height="41.957"
                      viewBox="0 0 50.74 41.957"
                    >
                      <g transform="translate(-297.5 -1435.771)">
                        <path
                          data-name="パス 186"
                          d="M-3567.73,1909l20.625,20.625-20.625,20.625"
                          transform="translate(3894.639 -472.875)"
                          fill="none"
                          stroke="#767676"
                          stroke-width="1"
                        ></path>
                        <line
                          data-name="線 1"
                          x1="50.224"
                          transform="translate(297.5 1457.125)"
                          fill="none"
                          stroke="#707070"
                          stroke-width="1"
                        ></line>
                      </g>
                    </svg>
                  </nuxt-link>
                </div>
              </div>
            </div>
          </section>
          <!-- <p>{{ posts }}</p> -->
        </main>
        <Footer />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "~/components/card.vue";
import news_card from "~/components/news_card.vue";
import { createClient } from "~/plugins/contentful.js";
const client = createClient();
export default {
  transition: "slide-left",
  components: {
    Card,
    news_card
  },
  computed: {
    is_news_visible: function(j) {
      console.log(j);
      return true;
    },
    news_ary: function() {
      console.log(this.posts.length);
      let _ary = [];
      let n = 0;
      for (let i in this.posts) {
        console.log(this.posts[i].sys.contentType.sys.id);
        this.posts[i].key_id = 1*i;
        if (this.posts[i].sys.contentType.sys.id == "news" && n < 2) {
          _ary.push(this.posts[i]);
        }
      }
      return _ary;
    },
    works_ary: function() {
      console.log(this.posts.length);
      let _ary = [];
      let n = 0;
      for (let i in this.posts) {
        console.log(this.posts[i].sys.contentType.sys.id);
        this.posts[i].key_id = 1*i;
        if (this.posts[i].sys.contentType.sys.id == "works" && n < 2) {
          _ary.push(this.posts[i]);
        }
      }
      return _ary;
    }
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

<style></style>
