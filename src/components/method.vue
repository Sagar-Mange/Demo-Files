<template>
    <div>
        <input value="Date" type="submit" @click.prevent="hello">
        {{message}}
    </div>
</template>

<script>
export default {
  data () {
    return {
      firstname: 'sagar',
      lastname: 'mange',
      message: ''
    }
  },
  methods: {
    hello: function () {
      console.log('Method called this times', this.message = Date())
      // return this.message
    }
  }
}
</script>
<style scoped>
</style>
