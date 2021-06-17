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
