<template>
    <img src='../assets/logo.png' alt='restaurant logo'/>
    <h1>Sign Up</h1>
    <form class='inputs'>
        <input type='text' v-model='name ' placeholder='Enter your name'/>
        <input type='mail' v-model='email' placeholder='Enter your email'/>
        <input type='password' v-model='password' placeholder='Enter your password'/>
        <button v-on:click="signUp">Sign Up</button>
    </form>
    <p>
        <router-link to='login'>Login</router-link>
    </p>
</template>
<script>
    
    import axios from 'axios'

    export default{

        name:'SignUp',
        data(){
            return{
                name:'',
                email:'',
                password:''
            }
        },
        methods:{
          async signUp(e){
                e.preventDefault(); 
                 let result = await axios.post('http://localhost:3000/users', {
                    name:this.name,
                    email:this.email,
                    password:this.password
                })

                if(result.status == 201){
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
