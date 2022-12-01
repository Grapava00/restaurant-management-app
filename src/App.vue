<template>
 <router-view />
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
body{
  margin:0;
  padding:0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
img{
  width: 200px
}

form{
  display:flex;
  flex-direction:column;
  align-items:center;
}

.form-add{
  margin-top:100px;
}

input{
  width: 250px;
  height: 29px;
  padding-left: 10px;
  caret-color: #b92c2c;
  border: 2px solid lightblue;
  margin-bottom:15px; 
  border-radius:5px;
}

input:focus{
  outline:none;
  border: 2px solid crimson;
  box-shadow:none;
}

button{
   width: 265px;
  border: none;
  padding: 10px 0;
  border-radius: 5px;
  cursor:pointer;
}

button:hover{
  background-color: lightblue;
}

a{
  text-decoration: none;
  color: black;
  
}

a:hover{
  color: gray;
}
</style>
