<template>
    <header>
        <nav>
            <ul>
                <li><router-link to='/'>Home</router-link></li>
                <li><router-link to='add'>Add restaurant</router-link></li>
                <li><a href="#" v-on:click="logOut">Logout</a></li>
            </ul>
        </nav>
    </header>
</template>
<script>
    export default{
        name:"HeaderSec",
        methods:{
            logOut(){
                localStorage.clear()
                this.$router.push({name:'LoginPage'})
                
            }
        }
    }
</script>
<style>

header{
    background-color: #e33b3b;
}

ul{
    list-style: none;
    display: flex;
    flex-wrap:wrap;
    margin: 0;
    padding: 10px 0;
  }
  
  li{
    margin-left:15px
  }

  ul a{
    color: white;
  }

  ul a:hover{
    color: black;
  }
</style>