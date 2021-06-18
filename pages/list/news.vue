<template>
  <div class="wrap-all">
    <div id="wrap-outer">
      <Header />
      <div id="wrap" class=" typesquare_option typesquare_option">
        <div id="content" class="News & Journal typesquare_option">
          <div
            id="post-96"
            class="post-96 page content_wrap_outer container two-cols-layout typesquare_option"
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
                  <div class="title-wrap typesquare_option">
                    <h1 class="title-wrap-tit pr_font-Theinhardt">
                      {{ title_h1 }}
                    </h1>
                  </div>

                  <div
                    id="content_wrap"
                    class="col-md-9 col-sm-9 typesquare_option"
                  >
                    <div
                      class="container-masonry ux-portfolio-spacing-40 ux-portfolio-1col   container typesquare_option"
                      data-template="blog-masonry"
                    >
                      <div class="masonry-list isotope  typesquare_option">
                        <list_sec
                          v-for="(post, i) in list_ary"
                          :key="i"
                          :category="post.fields.category"
                          :title="post.fields.title"
                          :thumbnail="post.fields"
                          :id="post.sys.id"
                          :date="post.sys.updatedAt"
                          :post="post"
                          :key_id="post.key_id"
                          :update="post.fields.date"
                          :category_id="category_name"
                          :tag_list='tag_list_flg'
                        />
                      </div>
                      <!-- {{ list_ary }} -->
                      <div
                        class="clearfix pagenums tw_style page_twitter typesquare_option"
                        data-pagetext="LOAD MORE ARTICLES"
                        data-loadingtext="LOADING..."
                      >
                        <a
                          class="tw-style-a ux-btn ux-page-load-more pr_font-Theinhardt pr_fr-news-ux-page-load-more"
                          data-pageid="96"
                          data-max="26"
                          data-paged="2"
                          href="#"
                          >LOAD MORE ARTICLES</a
                        >
                      </div>
                    </div>
                    <div class="container"></div>
                  </div>

                  <div class="entry pr_fr-news-det-entry typesquare_option">
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
                          <side_tag
                        v-for="(_t, i) in slide_tag_list"
                        :key="i"
                        :tag="_t"
                        :category="category_name"
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
                        :category="category_name"
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
// import { documentToHtmlString } from "@contentful/rich-text-html-renderer";
import { createClient } from "~/plugins/contentful.js";
import side_tag from "~/components/side_tag.vue";
import list_sec from "~/components/list_sec.vue";
import archive from "~/components/archive.vue";
const client = createClient();
export default {
  components: {
    list_sec,
    side_tag,
    archive
  },
  data: function() {
    return {
      category_name: "news",
      tag_list_flg: true,
      title_h1_archive_flg:false,
    };
  },
  computed: {
    params: function() {
      return this.$route.params;
    },
    model_type: function() {
      return "test";
    },
    list_ary: function() {
      // console.log(this.posts.length);
      // console.log(this.$route.query.id)
      // console.log(this.$route.params)
      this.title_h1_archive_flg = false;
      let _ary = [];
      let n = 0;
      for (let i in this.posts) {
        // console.log(this.posts[i].sys.contentType.sys.id);
        this.posts[i].key_id = i;
        if (this.posts[i].sys.contentType.sys.id == this.category_name) {
          if (!this.$route.query.tag || this.$route.query.tag == "ALL") {
            let _date_yyyy_mm = this.datetostr(this.posts[i].fields.date, "YYYY_MM", false)

            // console.log(this.$route.query.archive);
            // console.log(_date_yyyy_mm);
            if(!this.$route.query.archive){
              _ary.push(this.posts[i]);
            }else if(this.$route.query.archive == _date_yyyy_mm){
              _ary.push(this.posts[i]);
              this.title_h1_archive_flg = true;
              // this.title_h1 = 'ARCHIVES'
            }
            
          } else {
            // console.log(this.posts[i].fields.tags);
            if (!this.posts[i].fields.tags) {
              return;
            }
            for (let j in this.posts[i].fields.tags) {
              if (this.posts[i].fields.tags[j] == this.$route.query.tag) {
                this.tag_list_flg = false;
                _ary.push(this.posts[i]);
              }
            }
          }
        }
      }
      return _ary;
    },
    archive_list: function() {
      let arr = [];
      for (let i in this.posts) {
        if(this.posts[i].sys.contentType.sys.id == this.category_name){
          // return
       
        // console.log(this.datetostr(this.posts[i].fields.date, "YYYYMM", false));
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
      } }
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
        if (this.posts[i].sys.contentType.sys.id == this.category_name) {
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
    },
    title_h1: function(params) {
      // console.log(this.$route.query);
      if(this.title_h1_archive_flg){
        return "ARCHIVE"
      }
      if (this.$route.query.tag && this.$route.query.tag != "ALL") {
        return this.$route.query.tag.toUpperCase();
      } else {
        return this.category_name.toUpperCase();
      }
    }
  },
  methods: {
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
