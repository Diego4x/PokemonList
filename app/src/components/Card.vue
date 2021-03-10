<template>
<div>
    <div class="card mb-3" style="max-width: 540px;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="#" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">Nome: {{name}}</h5>
        <p class="card-text">Weight:</p>
        <p class="card-text">Height: </p>
         <button class="btn btn-primary" @click="pokeInfo()">Mais informacoes</button>
      </div>
    </div>
  </div>
</div>
</div>
</template>
<script>
export default {
  name: 'Card',
  data(){
    return {
      infos: []
    }
  },
  props: {
    name: String,
    id: Number
  },
  methods: {
      pokeInfo(){
        const url = 'https://pokeapi.co/api/v2/pokemon/'
        fetch(url + this.id)
        .then(response => response.json())
    .then(data => {
      this.infos = data
    })
    .catch(err => console.log(err));
      }
  }
}
</script>
