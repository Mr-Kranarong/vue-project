<template>
    <div class="container">
        <div class="card" v-for="archive in items" :key="archive.id">
            <h3>{{archive.date}} : {{archive.time}}</h3>
            <ul v-for="task in archive.tasks" :key="task.id">
                <li>{{task.id}} - {{task.title}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardList',
    props: ['items'],
    created(){
        console.log(this.items)
    }
}
</script>

<style>
    li{
        list-style: none;
    }
    h3{
        border: 1px solid black;
    }
    .card{
        border: 1px solid black;
        margin: 50px auto;
        width: 600px;
        background-color: white;
        transition: .3s;
    }
    .card:hover{
        transform: scale(1.5);
        transition: .3s;
    }
</style>

