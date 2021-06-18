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
                      <li class="cat-item cat-item-51">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/feature/"
                        >
                        </a>
                      </li>
                      <li class="cat-item cat-item-20 typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/news/"
                          class=" typesquare_option"
                          >ALL</a
                        >
                      </li>
                      <li class="cat-item cat-item-26 typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/event/"
                          class=" typesquare_option"
                          >EVENT</a
                        >
                      </li>
                      <li class="cat-item cat-item-1 typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/journal/"
                          class=" typesquare_option"
                          >JOURNAL</a
                        >
                      </li>
                      <li class="cat-item cat-item-28 typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/media-2/"
                          class=" typesquare_option"
                          >MEDIA</a
                        >
                      </li>
                      <li class="cat-item cat-item-29 typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/press-2/"
                          class=" typesquare_option"
                          >PRESS</a
                        >
                      </li>
                      <li class="cat-item cat-item-25 typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/report/"
                          class=" typesquare_option"
                          >REPORT</a
                        >
                      </li>
                    </ul>
                  </li>
                  <li class="widget-container widget_archive typesquare_option">
                    <h3 class="widget-title typesquare_option">
                      <span class="widget-title-inn typesquare_option"
                        >アーカイブ</span
                      >
                    </h3>
                    <ul class=" typesquare_option">
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2021/04/"
                          class=" typesquare_option"
                          >2021年4月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/11/"
                          class=" typesquare_option"
                          >2020年11月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/10/"
                          class=" typesquare_option"
                          >2020年10月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/09/"
                          class=" typesquare_option"
                          >2020年9月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/08/"
                          class=" typesquare_option"
                          >2020年8月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/07/"
                          class=" typesquare_option"
                          >2020年7月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/06/"
                          class=" typesquare_option"
                          >2020年6月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/05/"
                          class=" typesquare_option"
                          >2020年5月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/04/"
                          class=" typesquare_option"
                          >2020年4月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/03/"
                          class=" typesquare_option"
                          >2020年3月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/02/"
                          class=" typesquare_option"
                          >2020年2月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2020/01/"
                          class=" typesquare_option"
                          >2020年1月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/12/"
                          class=" typesquare_option"
                          >2019年12月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/11/"
                          class=" typesquare_option"
                          >2019年11月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/10/"
                          class=" typesquare_option"
                          >2019年10月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/09/"
                          class=" typesquare_option"
                          >2019年9月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/08/"
                          class=" typesquare_option"
                          >2019年8月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/07/"
                          class=" typesquare_option"
                          >2019年7月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/05/"
                          class=" typesquare_option"
                          >2019年5月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/04/"
                          class=" typesquare_option"
                          >2019年4月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/03/"
                          class=" typesquare_option"
                          >2019年3月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/02/"
                          class=" typesquare_option"
                          >2019年2月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2019/01/"
                          class=" typesquare_option"
                          >2019年1月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/12/"
                          class=" typesquare_option"
                          >2018年12月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/11/"
                          class=" typesquare_option"
                          >2018年11月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/10/"
                          class=" typesquare_option"
                          >2018年10月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/09/"
                          class=" typesquare_option"
                          >2018年9月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/08/"
                          class=" typesquare_option"
                          >2018年8月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/07/"
                          class=" typesquare_option"
                          >2018年7月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/06/"
                          class=" typesquare_option"
                          >2018年6月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/05/"
                          class=" typesquare_option"
                          >2018年5月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/02/"
                          class=" typesquare_option"
                          >2018年2月</a
                        >
                      </li>
                      <li class=" typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/2018/01/"
                          class=" typesquare_option"
                          >2018年1月</a
                        >
                      </li>
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
import list_sec from "~/components/list_sec.vue";
const client = createClient();
export default {
  components: {
    list_sec
  },
  data: function() {
    return {
      category_name: "news",
      tag_list_flg: true
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
      let _ary = [];
      let n = 0;
      for (let i in this.posts) {
        // console.log(this.posts[i].sys.contentType.sys.id);
        this.posts[i].key_id = i;
        if (this.posts[i].sys.contentType.sys.id == this.category_name) {
          if (!this.$route.query.tag || this.$route.query.tag == "ALL") {
            _ary.push(this.posts[i]);
          } else {
            console.log(this.posts[i].fields.tags);
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
    title_h1: function(params) {
      // console.log(this.$route.query);
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
