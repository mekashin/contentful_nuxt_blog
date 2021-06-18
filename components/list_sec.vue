<template>
  <section class="grid-item grid-item-standard typesquare_option">
    <div class="grid-item-inside typesquare_option">
      <nuxt-link
        :to="'/content/' + post.sys.contentType.sys.id + '?id=' + key_id"
        class="ux-lazyload-wrap"
      >
        <img
          class="ux-lazyload-img lazy"
          style="display: block;"
          width="1148"
          height="680"
          :src="post.fields.thumbnail.fields.file.url"
        />
      </nuxt-link>
      <div class="gird-blog typesquare_option">
        <div class="gird-blog-meta gird-blog-cate pr_font-Theinhardt">
          <span class="">IN </span>
          <tag
            v-for="(_t, i) in tag_list"
            :key="i"
            :tag="_t"
            :category="category_id"
          />
        </div>
        <h2 class="gird-blog-tit pr_fr-news-arvhive-tit typesquare_option">
          <nuxt-link
            :to="'/content/' + post.sys.contentType.sys.id + '?id=' + key_id"
            class="wrapper"
          >
            {{ post.fields.thumbnail.fields.url }} {{ post.fields.category }}
            <br v-if="post.fields.category" />
            {{ datetostr(post.fields.date, "M月D日", false) }}
            <span v-if="post.fields.date"> </span> {{ title }}</nuxt-link
          >
        </h2>
        <div class="gird-blog-meta gird-blog-date typesquare_option">
          <span class="article-meta-date pr_font-Theinhardt">{{
            datetostr(post.fields.date, "YYYY.M.D", false)
          }}</span>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import tag from "~/components/tag.vue";
export default {
  components: {
    tag
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
  computed: {
    thumbnail: function() {
      return this.post.fields.thumbnail.fields;
    },
    tag_list:function (params) {
        // console.log(this.post.fields);        
        return this.post.fields.tags
    }
  },
  props: {
    category: {
      type: String,
      default: ""
    },
    title: {
      type: String,
      default: ""
    },
    id: {
      type: String,
      default: ""
    },
    date: {
      type: String,
      default: ""
    },
    key_id: {
      //   type: Number,
      default: 0
    },
    post: {
      default: 0
    },
    category_id: {
      type: String,
      default: ""
    },
    // tag_list: {
    //   type: Boolean,
    //   default: true
    // }
  }
};
</script>
