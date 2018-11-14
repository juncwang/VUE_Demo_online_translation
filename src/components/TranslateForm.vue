<template>
  <div id="translateForm">
      <div>
          <form v-on:submit="formSubmit">
            <input type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容" />
            <select v-model="lang">
                <option value="en">English</option>
                <option value="ru">Russian</option>
                <option value="ko">Korean</option>
                <option value="ja">Janpenese</option>
            </select>
            <input type="submit" value="翻译" />
        </form>
      </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data:function(){
      return {
          textToTranslate: "",
          lang: "en"
      }
  },
  methods: {
      formSubmit:function(e){
          this.$emit("formSubmit", this.textToTranslate, this.lang)
          e.preventDefault()
      }
  }
}
</script>

