<template>
    <div class="text-center" id="app">
        <h1>Translator</h1>
        <h5>Powered by Vue.js</h5>
        <translateForm v-on:formSubmit="translateText"></translateForm>
        <translateOutput v-bind:translatedText="translatedText"></translateOutput>
    </div>
</template>

<script>
    import TranslateForm from './components/TranslateForm.vue';
    import TranslateOutput from './components/TranslateOutput.vue'
    export default {
        name: 'app',
        components:{
            TranslateForm,
            TranslateOutput
        },
        data: function () {
            return {
                translatedText: ''
            };
        },
        methods:{
            translateText: function(text,lang) {
                this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate',{
                    params:{
                        key: 'trnsl.1.1.20171109T191618Z.4eb28a9a42351690.6af99f114a4ac9c65b54cd53a256eaf75cd13bbf',
                        text:text,
                        lang:lang
                    }
                }).then((response) =>{
                    this.translatedText = response.body.text[0];
                });
            }
        }
    }
</script>

<style>
body{
    background:#fefefe;
}
</style>
