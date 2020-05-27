<template>
    <CardList :items="archives" />
</template>

<script>
import axios from 'axios'
import CardList from '../components/CardList'
export default {
    name: 'ArchivePage',
    components:{
        CardList
    },
    async created(){
        let {data} = await axios.get('http://localhost:3000/archives')
        console.log("axios ::: ", data)
        this.archives = data;
    },
    data(){
        return{
            archives:[]
        }
    }
}
</script>

