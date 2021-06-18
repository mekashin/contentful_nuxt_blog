<template>
  <li
    class="pr_fr-workslist-item js_fr_work_slug_search_target  branding creative webconsulting"
    data-postid="4636"
  >
    <nuxt-link
      :to="'/content/' + post.sys.contentType.sys.id + '?id=' + key_id"
      class="ux-lazyload-wrap" style="background-color: #fff;"
    >
      <div class="pr_fr-workslist-list-img" style="height:240px">
        <img :src="post.fields.thumbnail.fields.file.url" />
      </div>
      <div class="pr_fr-workslist-list-cont">
        <span
          class="pr_fr-workslist-list-cont-ttl js_pr_font-judge pr_font-Theinhardt"
          >{{ title }}</span
        >
        <ul class="pr_fr-workslist-list-cont-cat pr_sp-none pr_font-Theinhardt">
          <tag
            v-for="(_t, i) in tag_list"
            :key="i"
            :tag="_t"
            :category="category_id"
          />
        </ul>
      </div>
    </nuxt-link>
  </li>
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
