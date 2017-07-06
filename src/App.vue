<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutPut v-text="translatedText"></TranslateOutPut>

  </div>
</template>

<script>
import TranslateForm from './components/TranslanteForm.vue'
import TranslateOutPut from './components/TranslateOutPut.vue'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutPut
  },
  data: function () {
    return{
        translatedText:''
    }
  },

  methods:{
      translateText: function (text,language) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170706T072005Z.9ba52adfebf96689.740841e073d6b076b4798784be3a65da2becc889&lang='+language+'&text='+text)
          .then((response) => {
            this.translatedText = response.body.text[0];
          });
      }
  }
}
</script>

<style>
#app {

}
</style>
