<template>
  <li class="newsList-item typesquare_option">
    <nuxt-link :to="key_id + '/' + post.sys.contentType.sys.id" class="wrapper">

    </nuxt-link>
  </li>
</template>
<script>
export default {

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
