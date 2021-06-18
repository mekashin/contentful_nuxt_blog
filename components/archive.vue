<template>
  <li class="cat-item cat-item-20 typesquare_option">
    <nuxt-link :to="'/list/' + category + '?archive=' + tag" class="grid-meta-a">
      {{ date }}
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
    tag: {
      type: String,
      default: ""
    }
  },
  computed: {
      date: function() {
      return this.tag.split('_')[0] + '年' + Number(this.tag.split('_')[1]) + '月'
    },
  }
};
</script>
