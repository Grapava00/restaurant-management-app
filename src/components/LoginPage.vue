<template>
    <img src='../assets/logo.png' alt='restaurant logo'/>
    <h1>Login</h1>
    <form class='inputs'>
        <input type='mail' v-model='email' placeholder='Enter your email'/>
        <input type='password' v-model='password' placeholder='Enter your password'/>
        <button v-on:click="login">Login</button>
    </form>
    <p>
        <router-link to='sign-up'>Sign up</router-link>
    </p>
</template>
<script>
import axios from 'axios'
    export default{
        
        name:'LoginPage',
        data(){
            return{
                email:'',
                password:''
            }
        },
        methods:{
           async login(e){
                e.preventDefault();
                let result= await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`)
                if(result.status==200 && result.data.length>0 ){
                    localStorage.setItem("user-info", JSON.stringify(result.data))
                    this.$router.push({name:"HomePage"})
                }
            }
        },
        mounted(){
            let user = localStorage.getItem('user-info')
            if(user){
                this.$router.push({name:"HomePage"})
            }
        }
    }
</script>