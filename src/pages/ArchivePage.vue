<template>
    <CardList :items="archives" />
</template>

<script>
import CardList from '../components/CardList'
export default {
    name: 'ArchivePage',
    components:{
        CardList
    },
    data(){
        return{
            archives:[
                {
                    date: "25-05-2020",
                    time: "17:00",
                    tasks: [
                        {
                            id:1,
                            title:"Item A",
                            status:"done"
                        },
                        {
                            id:2,
                            title:"Item B",
                            status:"done"
                        }
                    ]
                },
                {
                    date: "26-05-2020",
                    time: "18:00",
                    tasks: [
                        {
                            id:3,
                            title:"Item C",
                            status:"done"
                        },
                        {
                            id:4,
                            title:"Item D",
                            status:"done"
                        }
                    ]
                }
            ]
        }
    }
}
</script>

