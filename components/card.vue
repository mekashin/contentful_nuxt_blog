<template>
<div>
<hr/>
  <nuxt-link
    :to="'/content/' + post.sys.contentType.sys.id +'?id=' + key_id"
    class="wrapper"
  >
    <article class="card">
      <h1 class="card_title">{{ title }}</h1>
      <p>{{key_id}}</p>
      <p class="card_text">{{ id }}</p>
      <p class="card_date">{{ date }}</p>
      <p class="card_date">{{ post.sys.contentType.sys.id }}</p>
    </article>
  </nuxt-link>
</div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    id: {
      type: String,
      default: ''
    },
    date: {
      type: String,
      default: ''
    },
    key_id: {
      type: Number,
      default: 0
    },    
    post: {
      default: 0
    }
  }
}
</script>