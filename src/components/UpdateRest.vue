<template>
    <HeaderSec />
    <form class="form-add">
        <input v-model='name' name='name' placeholder="Enter restaurant name"/>
        <input v-model='address' name='address' placeholder='Enter restaurant address'/>
        <button v-on:click="add">update</button>
    </form>
</template>
<script>
import HeaderSec from './HeaderSec.vue'
import axios from 'axios'

export default{
    name:'UpdateRest',
    data(){
        return{
            name:'',
            address:''
        }
    },
    components:{
        HeaderSec
    },
    async mounted(){
        let result = await axios.get("http://localhost:3000/restaurants/"+this.$route.params.id)
        this.name = result.data.name
        this.address = result.data.address
    },
    methods:{
        async add(e){
            e.preventDefault();

            let result = await axios.put("http://localhost:3000/restaurants/"+this.$route.params.id,{
                name:this.name,
                address:this.address
            })

            if(result.status==200){
                this.$router.push({name:"HomePage"})
            }

        }
    }
}
</script>