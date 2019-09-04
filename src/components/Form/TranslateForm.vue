<template>
    <div id="translateForm">
        <form @submit.prevent="formSubmit">
            <div class="row d-flex justify-content-around">
            <!-- Card Input -->
            <div class="col-sm-3">
                <h3 class="text-center mb-3">Texto Original</h3>
                <div class="form-group">
                    <input name="wordInput" type="text" v-model="textToTranslate" 
                    class="form-control" placeholder="Digite uma palavra..."/>
                </div>
                <div class="form-group">
                    <select v-model="language" class="form-control">
                        <option value="en" selected>Inglês</option>
                        <option value="es">Espanhol</option>
                        <option value="ru">Russo</option>
                        <option value="ja">Japonês</option>
                    </select>
                </div>
                <button class="btn btn-primary btn-block" type="submit" value="Translate">Traduzir</button>
            </div>
            <!-- Fim do Card Input -->
            <!-- Resultado -->
            <div class="col-sm-3">
                <h3 class="text-center mb-3">Resultado</h3>
                <div class="text-center">
                    <slot />
                </div>
            </div>
            <!-- Fim do Resultado -->
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: 'translateForm',
    data() {
        return {
            textToTranslate: '',
            language: ''
        }
    },
    methods: {
        formSubmit(event) {
            this.$emit('formSubmit', this.textToTranslate, this.language);
        }
    },
    created() {
        this.language = 'en';
    },
}
</script>