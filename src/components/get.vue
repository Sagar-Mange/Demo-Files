<template>
<div style="padding-top:2%">
  <div>
  <input value="Fetch Data" type="submit" @click.prevent="fetchData"> <br>
  <input id="input" type="number" placeholder="Enter Your Id" v-model="newId" @keypress.enter="addTitle"> <br>
  <input id="input" type="text" placeholder="Enter Your Title" v-model="newTitle" @keypress.enter="addTitle"> <br>
  <input id="input" type="text" placeholder="Enter Your Updated Title" v-model="updatedTitle" @keypress.enter="handleUpdateTitle"> <br>
  <input id="input" type="text" placeholder="Enter Your Modified Title" v-model="modifiedTitle" @keypress.enter="handlemodifiedTitle"> <br>
  <input value="Delete Data" type="submit" @click.prevent="deleteTitle">

  </div>
  <div>
  <ul>
    <li v-for="user in users" :key="user">
      {{user.userId}} - {{user.title}}
    </li>
  </ul>
  </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      users: [],
      newTitle: '',
      newId: '',
      updatedTitle: '',
      modifiedTitle: ''
    }
  },
  methods: {
    fetchData () {
      const axios = require('axios')
      // Make a request for a user with a given ID
      axios.get('https://jsonplaceholder.typicode.com/posts')
        .then(response => {
          this.users = response.data
          console.log(this.users)
          // handle success
        })

        .catch(function (error) {
          // handle error
          console.log(error)
        })

        .finally(function () {
          // always executed
        })
    },
    addTitle () {
      const axios = require('axios')
      axios.post('https://jsonplaceholder.typicode.com/posts', { title: this.newTitle, userId: this.newId })
        .then(response => {
          this.users.push(response.data)
          this.newTitle = ''
          this.newId = ''
        // handle success
        })
    },
    handleUpdateTitle () {
      const axios = require('axios')
      axios.put('https://jsonplaceholder.typicode.com/posts/2', { title: this.updatedTitle })
        .then(response => {
          console.log(response.data)
          alert(JSON.stringify(response.data))
          // handle success
        })
    },
    handlemodifiedTitle () {
      const axios = require('axios')
      axios.patch('https://jsonplaceholder.typicode.com/posts/1', { title: this.modifiedTitle })
        .then(response => {
          console.log(response.data)
          alert(JSON.stringify(response.data))
          // handle success
        })
    },
    deleteTitle () {
      const axios = require('axios')
      axios.delete('https://jsonplaceholder.typicode.com/posts/1')
        .then(response => {
          alert(JSON.stringify(response.data))
          alert(JSON.stringify(this.users))
          // handle success
        })
    }
  }
}
</script>
<style scoped>
#input {
  width:15%;
  height:25px;
}
</style>
