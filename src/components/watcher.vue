<template>
    <div>
      <input value="changename" type="submit" @click.prevent="changename"> {{firstname}} {{lastname}}
    </div>
</template>

<script>
export default {
  data () {
    return {
      firstname: 'saaagar',
      lastname: 'mange'
    }
  },
  methods: {
    changename: function () {
      this.firstname = 'Sagar'
      console.log('method called this times')
      this.lastname = 'Mange'
    }
  },
  watch: {
    firstname: function () {
      console.log('watcher called this times', this.firstname, this.lastname)
      // return this.firstname
    }
  }
}
</script>
<style scoped>
</style>
