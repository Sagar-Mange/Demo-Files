<template>
<div id="app">
  <!-- <registration-Form> </registration-Form> -->
  <!-- <app-method> </app-method> -->
  <!-- <app-watcher> </app-watcher> -->
  <!-- <app-computed> </app-computed> -->
  <!-- <app-question></app-question> -->
  <!-- <app-get> </app-get> -->
  <!-- <app-Example> </app-Example> -->
  <!-- <app-Form></app-Form> -->
  <app-demo></app-demo>
</div>
</template>

<script>
// import registrationForm from './components/registrationForm.vue'
// import method from '@/components/method.vue'
// import watcher from '@/components/watcher.vue'
// import computed from '@/components/computed.vue'
// import get from '@/components/get.vue'
// import question from '@/components/question.vue'
// import Example from '@/components/Example.vue'
// import Form from '@/components/Form.vue'
import demo from '@/components/demo.vue'

export default {
  components: {
    // 'registration-Form': registrationForm,
    // 'app-method': method,
    // 'app-watcher': watcher,
    // 'app-computed': computed,
    // 'app-get': get,
    // 'app-question': question,
    // 'app-Example': Example,
    // 'app-Form': Form,
    'app-demo': demo
  },
  data () {
    return {
    }
  }
}
</script>
