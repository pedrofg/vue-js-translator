<template>
  <div id="app" class="text-center">
  <h1>Word Translator</h1>
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
  data: function () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText:function (text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170507T003208Z.6cbdcc9f29b6d618.8b740d9cea30ca3ec2dc96e028d08f4d8ec3c069&lang='+language+'&text=' + text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background: #fefefe;
}
</style>
