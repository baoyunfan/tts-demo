<template>
  <div class="container" id="inputForm">
    <!-- form id="speakForm" class="well" v-on:submit.prevent="inputFormSubmit" -->
    <form id="speakForm" class="well">
      <div class="row">
        <div class="form-group col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <label class="sr-only" for="formInput">Text</label>
          <textarea id="textInput" class="form-control" rows="8" placeholder="Enter text to read" v-model="textToRead"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
          <select class="form-control" v-model="voice">
            <option v-bind:value="voice" v-for="voice in voiceList">{{voice}}</option>
          </select>
        </div>
        <div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
          <input class="btn btn-warning btn-block" type='submit' value='Stop' v-on:click.prevent="stop"/>
        </div>
        <div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
          <input class="btn btn-primary btn-block" type='submit' value='🔊 Speak' v-on:click.prevent="speak"/>
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
      textToRead: 'As jazz was becoming more and more popular in the 1930s and 1940\'s, another new genre was starting to develop. Many African Americans were professional blues musicians, but making money wasn\'t easy. They formed small bands and looked for work in cheap bars and clubs. But to get work, they had to attract audiences. Most young people who went to these places thought blues was old-fashioned, so the bands had to develop a new style, and what they created was "rhythm and blues" (or R&B).',
      voice: 'UK English Female',
      voiceList: [],
    }
  },

  created () {
    let voices = responsiveVoice.getVoices()
    for (let v of voices) {
      this.voiceList.push(v.name)
    }
    // this.voiceList = [ ...new Set(this.voiceList) ] // sort and dedupe
    this.voice = this.voiceList[0];
  },

  methods: {
    speak: function () {
      responsiveVoice.speak(this.textToRead, this.voice)
      // this.$emit('speak', this.textToRead, this.voice)
    },

    stop: function () {
      responsiveVoice.cancel()
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
