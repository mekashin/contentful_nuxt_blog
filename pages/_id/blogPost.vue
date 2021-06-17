<template>
<p>{{params}}</p>
</template>

<script>
import { createClient } from '~/plugins/contentful.js'
export default {
//   data: function(){
//     return {
//       title:'Login',
//     };
//   },
  computed: {
      params:function() {
          return this.$route.params;          
      },
      model_type:function() {
          return "test";
      },
      // message: function() {
      //   let id = this.$route.params.id != undefined 
      //       ? this.$route.params.id : '*** no id ***';
      //   let pass = this.$route.params.pass != undefined 
      //       ? this.$route.params.pass : '*** no password ***';
      //   return 'ID：' + id  + '<br>PASS：' + pass;
      // },
  },
}
</script>