<template>
    <HeaderSec />
    <form class="form-add">
        <input v-model='name' name='name' placeholder="Enter restaurant name"/>
        <input v-model='address' name='address' placeholder='Enter restaurant address'/>
        <button v-on:click="add">add</button>
    </form>
</template>
<script>
import HeaderSec from './HeaderSec.vue'
import axios from 'axios'
export default{
    name:'AddRest',
    data(){
        return{
            name:'',
            address:''
        }
    },
    methods:{
        async add(e){
            e.preventDefault();
            let addRest=await axios.post('http://localhost:3000/restaurants',{
                name:this.name,
                address:this.address
            })
            if(addRest.status===201){
                this.$router.push({name:"HomePage"})
            }
        }
    },
    components:{
        HeaderSec
    }

}
</script>