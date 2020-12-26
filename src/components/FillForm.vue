<template>
    <div>
        <form @submit="sendForm">
            <input type="text" v-model="name" name="name" placeholder="enter your name">
            <input type="text" v-model="mail" name="mail" placeholder="mail">
            <textarea type="text" v-model="message" name="message" placeholder="write us"/>
            <input type="submit" value="Submit" class="btn">
        </form>    
    </div>
</template> 

<script>
export default {
    name: "FillForm",
    data() {
        return {
            name: '',
            mail: '',
            message: ''
        }
    },
    methods: {
        sendForm(e) {
            e.preventDefault(); 
            const newForm = {
                name: this.name,
                mail: this.mail,
                message: this.message
            }
            //up to parent
            this.$emit('send-form', newForm);
        }
    }
}
</script>

<style scoped>
form {
  /* Center the form on the page */
  margin: 0 auto;
  width: 300px;
  /* Form outline */
  padding: 1em;
  border: 1px solid #CCC;
  border-radius: 1em;
}
input, textarea {
  /* To make sure that all text fields have the same font settings
     By default, textareas have a monospace font */
  font: 1em sans-serif;

  /* Uniform text field size */
  width: 300px;
  box-sizing: border-box;

  /* Match form field borders */
  border: 1px solid #999;
}

input:focus,
textarea:focus {
  /* Additional highlight for focused elements */
  border-color: #000;
}

textarea {
  /* Align multiline text fields with their labels */
  vertical-align: top;

  /* Provide space to type some text */
  height: 5em;
}

</style>