<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/translateForm'
import TranslateOutput from './components/translateOutput'

export default {
  name: 'App',
  data:function(){
    return {
      translatedText: ""
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods: {
    translateText:function(text,lang){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181114T071256Z.6e6031fc9a39bfe7.9da1e0bdeda1abbb52832640ef3ed583c745aabc&lang=' + lang + '&text=' + text)
        .then((response) => { this.translatedText = response.body.text[0] })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
