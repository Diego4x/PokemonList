<template>
  <div class="App">
    <div class="form" >
        <input v-model="text" id="txt" type="text" class="form-control" placeholder="Pokemon" aria-label="Username" aria-describedby="addon-wrapping">
        <button type="button" class="btn btn-warning" @click="getData()">Send</button>
    </div>
   <div v-show="mostrar" class="card" style="width: 18rem;">
  <img :src="userProfilePic"  class="rounded mx-auto d-block"  alt="..." style="width: 85px">
  <div class="card-body">
  <ul class="list-group list-group-flush">
     <li class="list-group-item">Name: {{dados.name}}</li>
    <li class="list-group-item">Type: {{type}}</li>
    <li class="list-group-item">Altura: {{dados.height}}</li>
  </ul>
  </div>
</div>  
<div class="alert alert-warning alert-dismissible fade show" role="alert" v-show="error">
  <strong>Ops!</strong> Digite um nome de um Pokemon no campo a cima por favor
</div>
</div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
          dados : [],
          userProfilePic: "",
          type: "",
          text: "",
          error: false,
          mostrar: false
    }
  },
  methods:{
    getData(){
      const baseUrl = 'https://pokeapi.co/api/v2/pokemon/'
      const name = this.text
      name.toLowerCase()
      this.dados = []
      fetch(baseUrl + name)
    .then(response => response.json())
    .then(data => {
      this.dados = data
      this.type = data.types[0].type.name
      this.userProfilePic = `https://pokeres.bastionbot.org/images/pokemon/${data.id}.png`
      console.log(data);
    })
    .catch(err => console.log(err));
  
    if(!this.text){
      this.error = true
      this.mostrar = false
    }else{
      this.error = false
      this.mostrar = true
    }
    }

  }
}
</script>
<style scoped>
.App{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#txt{
  margin-right: 5px;
}
.form{
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin: 10px;
}
</style>

