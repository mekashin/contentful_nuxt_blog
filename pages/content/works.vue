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
                         {{ posts[key_id].fields.category }}<br v-if="posts[key_id].fields.category" />{{ datetostr(posts[key_id].fields.date,"YYYY年M月D日",false) }} {{ posts[key_id].fields.title }}
                      </h2>
                      <div class="article-meta clearfix"></div>
                    </div>
                  </div>

                  <div class="gird-blog-des typesquare_option">
                    <div
                      class="gird-blog-meta gird-blog-cate pr_font-Theinhardt"
                    >
                      <span class="">IN </span>
                      <a
                        href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/news/"
                        class="grid-meta-a"
                        >ALL</a
                      >
                      <a
                        href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/category/media-2/"
                        class="grid-meta-a"
                        >MEDIA</a
                      >
                    </div>
                    <div
                      class="gird-blog-meta gird-blog-date pr_font-Theinhardt"
                    >
                      <!-- <span class="article-meta-date">{{ datetostr(posts[key_id].fields.date,"YYYY.M.D",false) }}</span> -->
                    </div>
                  </div>

                  <div class="entry pr_fr-news-det-entry typesquare_option" v-html="rich_txt2html(posts[key_id].fields.contents)">
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
import { documentToHtmlString } from '@contentful/rich-text-html-renderer';
import { createClient } from "~/plugins/contentful.js";
const client = createClient();
export default {
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
        console.log(this.$route.query.id)
      return this.$route.query.id;
    },
    model_type: function() {
      return "test";
    }
    // message: function() {
    //   let id = this.$route.params.id != undefined
    //       ? this.$route.params.id : '*** no id ***';
    //   let pass = this.$route.params.pass != undefined
    //       ? this.$route.params.pass : '*** no password ***';
    //   return 'ID：' + id  + '<br>PASS：' + pass;
    // },
  },
  methods: {
    rich_txt2html:function (_d) {
        return documentToHtmlString(_d)
        
    },
    datetostr: function(d, format, is12hours) {
      var weekday = ["日", "月", "火", "水", "木", "金", "土"];
      if (!format) {
        format = "YYYY/MM/DD(WW) hh:mm:dd";
      }
      var date = new Date(d)
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
    },
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
