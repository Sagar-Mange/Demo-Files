<template>
<div>
    <div>
        <input value="Fetch Data" type="submit" @click.prevent="fetchData">
    </div>
    <ul v-for="(post, inx) in posts" :key="inx">
        <li >
         <a href="#"> {{post.title}} </a>
         </li>
         <app-demo2 :post="post"></app-demo2>
    </ul>
</div>
</template>

<script>
/* eslint-disable */
import demo2 from '@/components/demo2.vue'

export default {
  components: {
    'app-demo2': demo2
  },
  data () {
    return {
      posts: [],
      user: null
    }
  },
  methods: {
    fetchData () {
      const axios = require('axios')
      // Make a request for a user with a given ID
      axios.get('https://jsonplaceholder.typicode.com/posts')
        .then(response => {
          this.posts = response.data
        //   this.user = this.posts[1]
        //   console.log("user", this.user)
          // handle success
        })

        .catch(function (error) {
          // handle error
          console.log(error)
        })

        .finally(function () {
          // always executed
        })
    }
  }
}
</script>

<style scoped>
li{
    margin-left:30%;
    font-size:20px;
    list-style-type:none
}

</style>
