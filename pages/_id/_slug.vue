<template>
<div>
  <p>{{ params }}</p>
  
  <p>{{ posts[key_id].fields.title }}</p>
  </div>
</template>

<script>
import { createClient } from "~/plugins/contentful.js";
const client = createClient();
export default {
  //   data: function(){
  //     return {
  //       title:'Login',
  //     };
  //   },
  computed: {
    params: function() {
      return this.$route.params;
    },
    key_id: function() {
      return this.$route.params.id;
    },
    model_type: function() {
      return "test";
    }
    // message: function() {
    //   let id = this.$route.params.id != undefined
    //       ? this.$route.params.id : '*** no id ***';
    //   let pass = this.$route.params.pass != undefined
    //       ? this.$route.params.pass : '*** no password ***';
    //   return 'ID：' + id  + '<br>PASS：' + pass;
    // },
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
