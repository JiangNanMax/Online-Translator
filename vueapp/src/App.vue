<template>
  <div id="app">
      <h1>在线翻译</h1>
      <h5 class="text-muted">Vue + Bootstrap</h5>
      <translateForm v-on:Submit="translateText"></translateForm>
      <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data:function(){
      return{
          translatedText:""
      }
  },
  components: {
      TranslateForm,
      TranslateOutput
  },
  methods:{
      translateText:function(text,language){
          //alert(text);
          this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180521T123838Z.1e43e75ec24e69e0.c460acb87d2a98807bc6fa103d32fca627fb24be&lang='+language+'&text='+text)
            .then((response)=>{
                //console.log(response.body.text[0])
                this.translatedText=response.body.text[0]
            })
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
