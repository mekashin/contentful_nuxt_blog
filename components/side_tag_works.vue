<template>
  <li class="cat-item cat-item-20 typesquare_option">
    <nuxt-link :to="'/list/' + category + '?tag=' + tag" class="grid-meta-a">
      {{ tag }}
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
  }
};
</script>
