<template>
    <div>
        <center><h4>Comments</h4></center>
        <!-- <p>{{comments}}</p> -->
        <ul v-for="(comment, inx) in comments" :key="inx">
        <li >
         <span> {{comment.name}} </span>
         <button id="edit">Edit</button>
         </li>
    </ul>
    </div>
</template>

<script>
/* eslint-disable */
const axios = require('axios')
export default {
  props: ['post'],
  data () {
    return {
      comments: []
    }
  },
  created () {
        //    console.log(document.getElementById('edit'))
           this.getCommentsByPostId(this.post.id)
  },
  mounted () {
    //   console.log("mounted", document.getElementById('edit'))
  },
  methods: {
      getCommentsByPostId (id) {
          axios.get('https://jsonplaceholder.typicode.com/comments?postId=' + id)
            .then(response => {
                this.comments = response.data
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
