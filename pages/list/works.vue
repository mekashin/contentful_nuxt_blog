<template>
  <div class="wrap-all">
    <div id="wrap-outer">
      <Header />
      <div id="wrap" class=" typesquare_option typesquare_option">
        <div id="content" class="TOP typesquare_option">
          <div
            id="post-9"
            class="post-9 page type-page status-publish hentry typesquare_option"
          >
            <section class="pr_fr-workslist-area typesquare_option">
              <div class="pr_fr-workslist-inner typesquare_option">
                <h1
                  class="pr_fr-workslist-ttl pr_font-Theinhardt title-wrap-tit"
                >
                  {{ title_h1 }}
                </h1>
                <ul class="pr_fr-workslist-nav pr_font-Theinhardt">
  
                      <side_tag
                        v-for="(_t, i) in slide_tag_list"
                        :key="i"
                        :tag="_t"
                        :category="category_name"
                      />
                  <!--
			<li><a href="#">All</a></li>
			<li><a href="#">Branding</a></li>
			<li><a href="#">Website</a></li>
			<li><a href="#">Consulting</a></li>
			<li><a href="#">Promotion</a></li>
			<li><a href="#">Product</a></li>
			<li><a href="#">Training</a></li>
			 -->
                </ul>
                <!-- <div class="pr_fr-workslist-heading typesquare_option">
                  <div
                    class="pr_fr-workslist-h-img js_pr_bgtransfer-target"
                    style='background-image: url("http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/wp-content/uploads/2020/06/2020SS_TOC_main.jpg");'
                  >
                    <img
                      class="js_pr_bgtransfer-ref"
                      src="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/wp-content/uploads/2020/06/2020SS_TOC_main.jpg"
                      alt="naturaglacé 2020 SS touch on colors"
                    />
                  </div>
                  <dl class="pr_fr-workslist-h-det typesquare_option">
                    <dt class="pr_fr-workslist-h-dttl pr_font-Theinhardt">
                      naturaglacé 2020 SS touch on colors
                    </dt>
                    <dd class="pr_fr-workslist-h-dcont typesquare_option">
                      <div
                        class="pr_fr-workslist-h-date pr_font-midashigo typesquare_option"
                      >
                        2020.03 ｜ 株式会社ネイチャーズウェイ
                      </div>
                      <p
                        class="pr_fr-workslist-h-lead pr_font-midashigo typesquare_option"
                      >
                        2020年春新アイテムのカラー訴求キャンペーン
                        キービジュアルの制作、店頭ツールへの展開を担当。
                      </p>
                      <p></p>
                      <div class="pr_fl-com-section-more-btn typesquare_option">
                        <a
                          href="http://ec2-18-236-107-130.us-west-2.compute.amazonaws.com/works/naturaglace-2020-ss-touch-on-colors/"
                          class=" typesquare_option"
                          ><span class="pr_font-Theinhardt">DETAIL</span></a
                        >
                      </div>
                    </dd>
                  </dl>
                </div> -->
                <div id="js_pr_fr-move-work-slug-position"></div>

                <ul class="pr_fr-workslist-list pr_font-raleway">
                       <list_sec_works
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
                    :tag_list="tag_list_flg"
                  />
                </ul>
              </div>
            </section>
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
import side_tag from "~/components/side_tag_works.vue";
import list_sec_works from "~/components/list_sec_works.vue";
import archive from "~/components/archive.vue";
const client = createClient();
export default {
  components: {
    list_sec_works,
    side_tag,
    archive
  },
  data: function() {
    return {
      category_name: "works",
      tag_list_flg: true,
      title_h1_archive_flg: false
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
            let _date_yyyy_mm = this.datetostr(
              this.posts[i].fields.date,
              "YYYY_MM",
              false
            );

            // console.log(this.$route.query.archive);
            // console.log(_date_yyyy_mm);
            if (!this.$route.query.archive) {
              _ary.push(this.posts[i]);
            } else if (this.$route.query.archive == _date_yyyy_mm) {
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
        if (this.posts[i].sys.contentType.sys.id == this.category_name) {
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
      if (this.title_h1_archive_flg) {
        return "ARCHIVE";
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
