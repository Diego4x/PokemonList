<template>
  <div class="App">
    <div class="form" >
        <input v-model="text" id="txt" type="text" class="form-control" placeholder="Pokemon" aria-label="Username" aria-describedby="addon-wrapping">
        <button type="button" class="btn btn-warning" @click="getData()">Send</button>
    </div>
   <div class="card" style="width: 18rem;">
  <img :src="userProfilePic"  class="rounded mx-auto d-block"  alt="..." style="width: 85px">
  <div class="card-body">
  <ul class="list-group list-group-flush">
     <li class="list-group-item">Name: {{dados.name}}</li>
    <li class="list-group-item">Type: {{type}}</li>
  </ul>
  </div>
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
          text: ""
    }
  },
  methods:{
    getData(){
      const baseUrl = 'https://pokeapi.co/api/v2/pokemon/'
      const name = this.text
      this.dados = []
      fetch(baseUrl + name)
    .then(response => response.json())
    .then(data => {
      this.dados = data
      this.type = data.types[0].type.name
      this.userProfilePic = `https://pokeres.bastionbot.org/images/pokemon/${data.id}.png`
    })
    .catch(err => console.log(err));
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

