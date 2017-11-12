<template>
    <div class="row" id="translateForm">
        <div class="col-md-6 offset-md-3">
            <form class="form-inline justify-content-center" v-on:submit.prevent="formSubmit">
                <input class="form-control mb-2 mr-sm-2 mb-sm-0" type="text" v-model="textToTranslate" placeholder="Enter a word..">
                <select class="form-control mb-2 mr-sm-2 mb-sm-0" v-model="language">
                    <option selected value="ru">Russian</option>
                    <option value="es">Spanish</option>
                    <option value="ja">Japanese</option>
                    <option value="it">Italian</option>
                </select>
                <input class="btn btn-primary mb-2 mr-sm-2 mb-sm-0" type="submit" value="Translate">
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'translateForm',
        data: function () {
            return {
                textToTranslate: '',
                language: ''
            }
        },
        created:function(){
            this.language = 'ru';
        },
        methods: {
            formSubmit() {
                this.$emit('formSubmit', this.textToTranslate, this.language);
            }
        }
    }
</script>

<style>

</style>
