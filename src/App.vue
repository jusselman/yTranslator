<template>
  <div id="app">

    <h1>Language Translator</h1>
    <h5>Powered by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr/translate?key=trnsl.1.1.20180919T152529Z.4b1f5bb2a2deb071.c6551219c2a3d008c642376cf2ee36a6f8ebc84b&lang=ru&text='+text)
      .then((response) => {

        this.translatedText = response.body;
      });

    }
  }
}
</script>

<style>
#app {

}
</style>
