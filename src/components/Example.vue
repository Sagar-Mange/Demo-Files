<template>
<div>
    <div>
        <input value="Fetch Data" type="submit" @click.prevent="fetchData"> <br>
        <input id="input" type="text" placeholder="Enter Your First Name" v-model="name" @keypress.enter="addName">
        <input id="input" type="text" placeholder="Enter Your last Name" v-model="name1" @keypress.enter="addName">
        <input id="input" type="text" placeholder="Enter Your Modified Name" v-model="modifiedName" @keypress.enter="handlemodifiedName">
        <input id="input" type="text" placeholder="Enter Your updated Name" v-model="updatedName" @keypress.enter="handleupdatedName">
    </div>
        <div>
        <ul>
            <li v-for="user in users" :key="user">
                {{user.firstname}} - {{user.lastname}}
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
      name: '',
      name1: '',
      modifiedName: '',
      updatedName: ''
    }
  },
  methods: {
    fetchData () {
      const axios = require('axios')
      // Make a request for a user with a given ID
      axios.get('http://192.168.2.65:3030/users')
        .then(response => {
          this.users = response.data.data
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
    addName () {
      const axios = require('axios')
      axios.post('http://192.168.2.65:3030/users', { firstname: this.name, lastname: this.name1 })
        .then(response => {
          this.users.push(response.data)
          this.name = ''
          this.name1 = ''
          console.log(this.name, this.name1)
        })
    },
    handlemodifiedName () {
      const axios = require('axios')
      axios.patch('http://192.168.2.65:3030/users/1S0ZvZOxSMrKCz5l', { lastname: this.modifiedName })
        .then(response => {
          console.log(response.data)
          alert(JSON.stringify(response.data))
        //   alert(JSON.stringify(this.users))
          // handle success
        })
    },
    handleupdatedName () {
      const axios = require('axios')
      axios.put('http://192.168.2.65:3030/users/1S0ZvZOxSMrKCz5l', { lastname: this.updatedName })
        .then(response => {
          console.log(response.data)
          alert(JSON.stringify(response.data))
        })
    }
  }
}
</script>

<style scoped>

</style>
