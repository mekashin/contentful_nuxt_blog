<template>
  <div class="wrap-all">
    <div id="wrap-outer">
      <Header />
      <div id="wrap" class=" typesquare_option typesquare_option">
        <div id="content" class=" typesquare_option">
          <div
            class="content_wrap_outer container two-cols-layout typesquare_option"
          >
            <div class="sidebar-layout row typesquare_option">
              <div
                id="content_wrap"
                class="col-md-9 col-sm-9 typesquare_option"
              >
                <article
                  id="post-5247"
                  class="post-5247 post type-post status-publish format-standard has-post-thumbnail hentry category-news category-media-2 typesquare_option"
                >
                  <div class=" title-wrap typesquare_option">
                    <div class="title-wrap-con typesquare_option">
                      <h2
                        class="title-wrap-tit pr_fl-news-title-wrap-tit typesquare_option"
                      >
                        {{ posts[key_id].fields.category
                        }}<br v-if="posts[key_id].fields.category" />{{
                          datetostr(
                            posts[key_id].fields.date,
                            "YYYY年M月D日",
                            false
                          )
                        }}
                        {{ posts[key_id].fields.title }}
                      </h2>
                      <div class="article-meta clearfix"></div>
                    </div>
                  </div>

                  <div class="gird-blog-des typesquare_option">
                    <div
                      class="gird-blog-meta gird-blog-cate pr_font-Theinhardt"
                    >
                      <span class="">IN </span>
                      <tag
                        v-for="(_t, i) in tag_list"
                        :key="i"
                        :tag="_t"
                        :category="category_id"
                      />
                    </div>
                    <div
                      class="gird-blog-meta gird-blog-date pr_font-Theinhardt"
                    >
                      <!-- <span class="article-meta-date">{{ datetostr(posts[key_id].fields.date,"YYYY.M.D",false) }}</span> -->
                    </div>
                  </div>

                  <div
                    class="entry pr_fr-news-det-entry typesquare_option"
                    v-html="rich_txt2html(posts[key_id].fields.contents)"
                  >
                    <!-- {{ rich_txt2html(posts[key_id].fields.contents) }}  -->
                  </div>
                  <!--End entry-->
                </article>
                <!--end article-->
              </div>
              <!--End content_wrap-->

              <aside
                id="sidebar-widget"
                class="col-md-3 col-sm-3 typesquare_option"
              >
                <ul class="sidebar_widget typesquare_option">
                  <li
                    class="widget-container widget_categories typesquare_option"
                  >
                    <h3 class="widget-title typesquare_option">
                      <span class="widget-title-inn typesquare_option"
                        >カテゴリー</span
                      >
                    </h3>
                    <ul class=" typesquare_option">
                      <!-- <li class="cat-item cat-item-51">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/feature/"
                        >
                        </a>
                      </li> -->
                      <side_tag
                        v-for="(_t, i) in slide_tag_list"
                        :key="i"
                        :tag="_t"
                        :category="category_id"
                      />
                    </ul>
                  </li>
                  <li class="widget-container widget_archive typesquare_option">
                    <h3 class="widget-title typesquare_option">
                      <span class="widget-title-inn typesquare_option"
                        >アーカイブ</span
                      >
                    </h3>
                    <ul class=" typesquare_option">
                      <archive
                        v-for="(_t, i) in archive_list"
                        :key="i"
                        :tag="_t"
                        :category="category_id"
                      />
                    </ul>
                  </li>
                </ul>
              </aside>
            </div>
          </div>
          <!--End content_wrap_outer-->
        </div>
        <Footer />
      </div>
    </div>
  </div>
</template>

<script>
import tag from "~/components/tag.vue";
import archive from "~/components/archive.vue";
import side_tag from "~/components/side_tag.vue";
import { documentToHtmlString } from "@contentful/rich-text-html-renderer";
import { createClient } from "~/plugins/contentful.js";
const client = createClient();
export default {
  components: {
    tag,
    side_tag,
    archive
  },
  props: {
    post: {
      default: 0
    }
  },
  data: function() {
    return {
      category_id: "works",
      tag_list_flg: true
    };
  },
  //   data: function(){
  //     return {
  //       title:'Login',
  //     };
  //   },
  computed: {
    params: function() {
      return this.$route.params;
    },
    key_id: function() {
      console.log(this.$route.query.id);
      return this.$route.query.id;
    },
    model_type: function() {
      return "test";
    },
    tag_list: function(params) {
      return this.posts[this.key_id].fields.tags;
    },
    archive_list: function() {
      let arr = [];
      for (let i in this.posts) {
        console.log(this.datetostr(this.posts[i].fields.date, "YYYYMM", false));
        let yyyymm = this.datetostr(
          this.posts[i].fields.date,
          "YYYY_MM",
          false
        );
        let arr_add_flg = 0;
        for (let j in arr) {
          if (arr[j] != yyyymm) {
            ++arr_add_flg;
          }
        }
        if (arr_add_flg == arr.length) {
          arr_add_flg = 0;
          arr.push(yyyymm);
        }
      }
      arr.sort(function(a, b) {
        if (a > b) return -1;
        if (a < b) return 1;
        return 0;
      });

      return arr;
    },
    slide_tag_list: function() {
      let arr = ["ALL"];
      for (let i in this.posts) {
        // console.log(this.category_id);
        if (this.posts[i].sys.contentType.sys.id == this.category_id) {
          // console.log( this.posts[i].fields.tags);
          for (let j in this.posts[i].fields.tags) {
            // console.log(this.posts[i].fields.tags[j]);
            let arr_add_flg = 0;
            for (let k in arr) {
              if (arr[k] != this.posts[i].fields.tags[j]) {
                ++arr_add_flg;
              }
            }
            if (arr_add_flg == arr.length) {
              arr_add_flg = 0;
              arr.push(this.posts[i].fields.tags[j]);
            }
            // arr_flg = false
            //   arr.push(this.posts[i].fields.tags[j])
          }
          this.posts[i].fields.tags;
        }
      }

      return arr;
    }
  },
  methods: {
    rich_txt2html: function(_d) {
      return documentToHtmlString(_d);
    },
    datetostr: function(d, format, is12hours) {
      var weekday = ["日", "月", "火", "水", "木", "金", "土"];
      if (!format) {
        format = "YYYY/MM/DD(WW) hh:mm:dd";
      }
      var date = new Date(d);
      var year = date.getFullYear();
      var month = date.getMonth() + 1;
      var day = date.getDate();
      var weekday = weekday[date.getDay()];
      var hours = date.getHours();
      var minutes = date.getMinutes();
      var secounds = date.getSeconds();

      var ampm = hours < 12 ? "AM" : "PM";
      if (is12hours) {
        hours = hours % 12;
        hours = hours != 0 ? hours : 12; // 0時は12時と表示する
      }

      var replaceStrArray = {
        YYYY: year,
        Y: year,
        MM: ("0" + month).slice(-2),
        M: month,
        DD: ("0" + day).slice(-2),
        D: day,
        WW: weekday,
        hh: ("0" + hours).slice(-2),
        h: hours,
        mm: ("0" + minutes).slice(-2),
        m: minutes,
        ss: ("0" + secounds).slice(-2),
        s: secounds,
        AP: ampm
      };

      var replaceStr = "(" + Object.keys(replaceStrArray).join("|") + ")";
      var regex = new RegExp(replaceStr, "g");

      var ret = format.replace(regex, function(str) {
        return replaceStrArray[str];
      });

      return ret;
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
