<template>
  <div class="App">
    <div class="form">
        <input id="txt" type="text" class="form-control" placeholder="Pokemon" aria-label="Username" aria-describedby="addon-wrapping">
        <button type="button" class="btn btn-warning">Send</button>
    </div>
    <Card></Card>
  </div>
</template>

<script>
import Card from './components/Card'
export default {
  name: 'App',
  components: {
    Card
  }
}
</script>
<style scoped>
.App{
  display: flex;
  flex-direction: row;
  justify-content: center;
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

