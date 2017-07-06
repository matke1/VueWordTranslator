<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form v-on:submit="formSubmit">

        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter word" >
        <select class="form-control" v-model="language">
          <option value="ru">Russian</option>
          <option value="fr">French</option>
          <option value="es">Spanish</option>
          <option value="bs">Bosnian</option>
          <option value="sr">Serbian</option>
          <option value="no">Norwegian</option>
          <option value="eu">Basque</option>
          <option value="th">Thai</option>
          <option value="tt">Tatar</option>
          <option value="uk">Ukrainian</option>
          <option value="cs">Czech</option>
          <option value="ja">Japanese</option>
        </select>
        <br>
        <input class="btn btn-primary" type="submit" value="Translate">

      </form>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data(){
        return{
            textToTranslate: '',
            language: ''
        }
    },
    created(){
        this.language = 'ru';
    },
    methods: {
        formSubmit(e){
            this.$emit('formSubmit', this.textToTranslate, this.language);
            e.preventDefault();
        }
    }

  }
</script>

<style>
  #app {

  }
</style>
