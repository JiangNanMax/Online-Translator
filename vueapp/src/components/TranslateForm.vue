<template>
  <div class="row" id="translateForm">
      <div class="col-md-12">
          <form id="transForm" class="well" v-on:submit="formSubmit">
              <input type="text" v-model="textTotranslate" placeholder="输入需要翻译的内容">
              <select v-model="language">
                  <option value="en">English</option>
                  <option value="ru">Russian</option>
                  <option value="ko">Korean</option>
                  <option value="ja">Japanese</option>
              </select>
              <input class="btn btn-primary" type="submit" name="" value="翻译">
          </form>
      </div>
  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
      return{
          textTotranslate:"",
          language:""
      }
  },
  methods:{
      formSubmit:function(e){
          //alert(this.textTotranslate);
          this.$emit("Submit",this.textTotranslate,this.language);
          e.preventDefault();
      }
  },
  created:function(){
      this.language="en";
  }
}
</script>

<style>
    #transForm{
        border-radius: 8px;
        border:1px #ccc solid;
    }
</style>
