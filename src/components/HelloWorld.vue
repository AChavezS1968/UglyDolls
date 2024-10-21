<template>
  <div class="hello">
    <center>
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>{{ msg }}</h1>
    <br>
    <h2><b>
      Luce lo exclusivo: Aretes y Anillos Artesanales Únicos
      </b>
    </h2> 
  </center>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
hello {
  border: 1px solid #ccc;
  padding: 10px;
  width: 200px;
}
</style>
