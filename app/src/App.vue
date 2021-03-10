<template>
  <div class="App">
    <div class="form" >
        <input v-model="text" id="txt" type="text" class="form-control" placeholder="Pokemon" aria-label="Username" aria-describedby="addon-wrapping">
        <button type="button" class="btn btn-warning" @click="getData()">Send</button>
    </div>
    <Card 
      :name = "dados.name"
      :id = "dados.id"
     />
  </div>
</template>

<script>
import Card from './components/Card'
export default {
  name: 'App',
  components: {
    Card
  },
  data(){
    return {
          dados : [],
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

