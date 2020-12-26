<template>
  <div id="app">
    <ul>
        <li v-for="form in forms" :key="form"> 
            {{form}}
        </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Forms',
  components: {
    
  },
  data: function() {
    return {
      forms: [] 
    }
  },
  methods: {
    created() {
        axios.get('http://localhost:8081/usersForm')
        .then(res => this.forms = res.data)
        .catch(err => console.log(err))
    }
  },
  beforeMount() {
      this.created()
  }
}
</script>

<style>
</style>