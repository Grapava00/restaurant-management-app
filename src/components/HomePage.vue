<template>
    <Header />
    <p>Hello, {{name}}</p>
    <table>
        <tr class="tr-des">
            <td>ნომერი</td>
            <td>ნაშრომი</td>
            <td>ნაშრომის აღწერა</td>
            <!-- <td>actions</td> -->
        </tr>
        <tr v-for='item in restaurants' :key='item.id'>
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.address}}</td>
            <!-- <td>
                <router-link :to="'/update/'+item.id">update</router-link>
                <button v-on:click="deleteRestaurant(item.id)">delete</button>
            </td> -->
        </tr>
    </table>
</template>

<script>
import Header from './HeaderSec.vue'
import axios from 'axios'

    export default{
        name:"HomePage",
        data(){
            return{
                name:'',
                restaurants:[]
            }
        },
        components:{
            Header
        }, 
        methods:{
            async deleteRestaurant(id){
                let result = await axios.delete('http://localhost:3000/restaurants/'+id)

                if(result.status==200){
                    this.loadData()
                }
                
                console.warn(result )
            },
            async loadData(){
                let user = localStorage.getItem('user-info')

                if(user !== null){
                    this.name=JSON.parse(user)[0].name
                }

                if(!user){
                    this.$router.push({name:"SignUp"})
                }

                let restaurantsList = await axios.get('http://localhost:3000/restaurants')

                if(restaurantsList.status==200){
                    this.restaurants = restaurantsList.data
                }
            }
        },
       async mounted(){
            this.loadData()
        }
    }
</script>
<style>
    .tr-des{
        background-color: lightslategray;
        color: bisque;
    }
    td{
        width: 200px;
        padding: 20px;
        border: 1px solid rgb(135, 20, 43);
    }

</style>