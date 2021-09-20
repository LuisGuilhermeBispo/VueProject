<template>
  <div>
    <h1>{{ title }}</h1>
    <h2 v-text="title"></h2>
    <ul>
      <li v-for="foto of fotos">
        <img v-bind:src="foto.url" :alt="foto.title">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: 'AluraPic',
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

</style>
