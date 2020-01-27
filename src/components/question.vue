<template>
<div>
    <div id="watch-example">
  <p>
    Ask a yes/no question:
    <input v-model="question">
  </p>
  <p>{{ answer }}</p>
</div>
</div>
</template>

/*eslint-disable */
<script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/lodash@4.13.1/lodash.min.js"></script>
<script>
export default {
    data() {
        return {
    question: '',
    answer: 'I cannot give you an answer until you ask a question!'
    }
    },
    watch: {
    // whenever question changes, this function will run
    question: function (newQuestion, oldQuestion) {
      console.log("this is working")
      this.answer = 'Waiting for you to stop typing...'
      var me = this
      setTimeout(function(){

        return me.getAnswer()

      },1000)
    }
  },
  methods: {
    getAnswer: function () {
      if (this.question.indexOf('?') === -1) {
        this.answer = 'Questions usually contain a question mark. ;-)'
        return
      }
      else if(!this.question.lastIndexOf('?')){
        console.log("this is not working")
        this.answer = 'Your Syntax Is Wrong'
        return
      }
      // else if(this.question.includes(/\?*$/g)){
      else {
      var str = this.question
      // this.answer = 'Not Valid'
      this.question = str.replace(/\?.$/g,"?")
      }
      this.answer = 'Thinking...'
      var vm = this
      const axios = require('axios')
      axios.get('https://yesno.wtf/api')
        .then(function (response) {
          vm.answer = response.data.answer
        })
        .catch(function (error) {
          vm.answer = 'Error! Could not reach the API. ' + error
        })
    }
}
}
</script>
<style scoped>

</style>
