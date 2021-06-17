<template>
  <li class="newsList-item typesquare_option">
    <nuxt-link :to="key_id + '/' + post.sys.contentType.sys.id" class="wrapper">
      <div class="newsList-item-thumbnail">
        <img
          width="1856"
          height="966"
          :src="post.fields.thumbnail.fields.file.url"
          class="attachment-post-thumbnail size-post-thumbnail wp-post-image"
          alt=""
          sizes="(max-width: 1856px) 100vw, 1856px"
        />
      </div>
      <h3 class="newsList-item-tit typesquare_option">
          {{post.fields.thumbnail.fields.url}}
        {{ post.fields.category }} <br v-if="post.fields.category" />
        {{ datetostr(post.fields.date,"M月D日",false) }} <span v-if="post.fields.date"> </span>
        {{ title }}
      </h3>
    </nuxt-link>
  </li>
</template>
<script>
export default {
  methods: {
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
  computed: {
      thumbnail:function(){
          return this.post.fields.thumbnail.fields
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
      type: Number,
      default: 0
    },
    post: {
      default: 0
    },
  }
};
</script>
