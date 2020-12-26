<template>
  <div id="app">
    <FillForm v-on:send-form="sendForm"/>
  </div>
</template>

<script>
import FillForm from '../components/FillForm.vue'
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    FillForm
  },
  data() {
    return {
      forms: [] 
    }
  },
  methods: {
    sendForm(newForm) {
        //post request
        const {name, mail, message} = newForm;

        axios.post('http://localhost:8081/postForm', {
          name,
          mail,
          message
        }).then(this.$router.push('forms'))
          .catch(err => console.log(err));
    }
  }
}
</script>

<style>
</style>
