<template>
  <nuxt-link :to="'/list/' + category + '?tag=' + tag" class="grid-meta-a">
    {{ tag }}
  </nuxt-link>
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
