<template>
    <div>
        {{reverseName}}
        {{reverseName}}
        {{reverseName}}
    </div>
</template>
<script>
export default {
  data () {
    return {
      fname: 'sagar',
      lname: 'mange'
    }
  },
  computed: {
    reverseName: function () {
      console.log('computed called this times', this.fname.split('').reverse().join(''))
      console.log('computed called this times', this.lname.split('').reverse().join(''))
      return this.fname.split('').reverse().join('')
    }
  }
}
</script>
<style scoped>
</style>
