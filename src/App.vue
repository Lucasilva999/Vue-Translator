<template>
  <div id="app">
    <div class="row">
      <div class="col-sm text-center my-4">
        <h5>Vue.Js e Yandex Translate API</h5>
        <h1>Tradutor de Palavras</h1>
        <hr>
      </div>
    </div>
    <TranslateForm @formSubmit="translateText">
        <TranslateOutput v-text="translatedText"/>
    </TranslateForm>
  </div>
</template>

<script>
import TranslateForm from '@/components/Form/TranslateForm.vue';
import TranslateOutput from '@/components/Form/TranslateOutput.vue';

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText(text, language) {
      fetch(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190904T163643Z.3c9bbe55afb60339.3582429c986c6a30102f60d3fcb20eb74f076e1e&lang=pt-${language}&text=${text}`)
      .then(res => res.json())
      .then(res => this.translatedText = res.text[0]);
    }
  },
}
</script>

<style>

</style>
