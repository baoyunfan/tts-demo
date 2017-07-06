<template>
  <div class="container" id="inputForm">
      <form id="speakForm" class="well" v-on:submit.prevent="inputFormSubmit">
        <div class="row">
          <div class="form-group col-xs-12 col-sm-12 col-md-12 col-lg-12">
            <label class="sr-only" for="formInput">Text</label>
            <textarea id="textInput" class="form-control" rows="5" placeholder="Enter text to read" v-model="textToRead"></textarea>
          </div>
        </div>
        <div class="row">
          <div class="form-group col-xs-12 col-sm-12 col-md-4 col-lg-4 col-md-offset-8 col-lg-offset-8">
            <input class="btn btn-primary btn-block" type='submit' value='🔊 Speak' />
          </div>
        </div>
      </form>
  </div>
</template>

<script>
export default {
  name: 'InputForm',
  data () {
    return {
      textToRead: ''
    }
  },
  methods: {
    inputFormSubmit: function () {
      this.$emit('inputFormSubmit', this.textToRead)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#textInput {
  width: 100%;
  resize: vertical;
}
#speakForm {
  border-radius: 10px;
  border: 2px #ccc solid;
}
</style>
