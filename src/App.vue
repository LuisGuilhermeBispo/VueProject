

<template>
  <div class="corpo">
    <h1 class="centralizado">{{ titulo }}</h1>
    <!-- <h2 v-text="titulo"></h2> -->

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of fotos">

        <meu-painel :titulo="foto.titulo">
            <img class="imagem-responsiva" v-bind:src="foto.url" v-bind:alt="foto.titulo">
            <!-- <img :src="foto.url" :alt="foto.titulo"> -->
        </meu-painel>

      </li>
    </ul>

  </div>
</template>

<script>
import Painel from './components/shared/painel/Painel.vue';

export default {

  components: {
    'meu-painel' : Painel
  },

  data() {
    return {
      titulo: 'AluraPic',
      fotos: [ ]
    }
  },

  created(){
    // let promise = this.$http.get('http://localhost:3000/v1/fotos');
    // promise.then(res => {

    //   res.json().then(fotos => this.fotos = fotos);
    // });

  this.$http.get('http://localhost:3000/v1/fotos')
    .then( res =>  res.json())
    .then( fotos => this.fotos = fotos, err => console.log(err));

  }
}
</script>

<style lang="scss">

  .corpo {
      font-family: Helvetica, sans-serif;
      width: 96%;
      margin: 0 auto;
  }
  .centralizado{
    text-align: center;
  }

  .lista-fotos{
    list-style: none;
  }
  .lista-fotos .lista-fotos-item{
    display: inline-block;
  }

  .imagem-responsiva {
    width: 100%;
  }
</style>
