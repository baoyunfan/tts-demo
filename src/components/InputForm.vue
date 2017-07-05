<template>
  <div class="row" id="inputForm">
    <div class="col-md-10 col-md-offset-1">
      <form id="speakForm" class="well form-inline" v-on:submit.prevent="inputFormSubmit">
        <div class="row">
          <div class="form-group col-md-10">
            <label class="sr-only" for="formInput">Input</label>
            <textarea id="textInput" class="form-control" placeholder="Enter text to read" v-model="textToRead"></textarea>
          </div>
          <div class="form-group col-md-2">
            <input class="btn btn-primary" type='submit' value='🔊 Speak' />
          </div>
        </div>
      </form>
    </div>
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
}
#speakForm {
  border-radius: 10px;
  border: 1px #ccc solid;
}
</style>
