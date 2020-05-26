<template>
    <div class="container">
        <div class="task-zone">
            <div class="drop-zone">
                <h1>What Need To Be Done</h1>
                <div class="drag-el" v-for="task in needToBeDone" :key="task.id">{{task.title}}</div>
            </div>
            <div class="drop-zone">
                <h1>Das Kapital</h1>
                <div class="drag-el" v-for="task in beingDone" :key="task.id">{{task.title}}</div>
            </div>
            <div class="drop-zone">
                <h1>What Has Been Done</h1>
                <div class="drag-el" v-for="task in hasBeenDone" :key="task.id">{{task.title}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TaskList',
    data(){
        return{
            tasks:[
                {
                    id: 1,
                    title: 'Item A',
                    status: 'HAS BEEN DONE'
                },
                {
                    id: 2,
                    title: 'Item B',
                    status: 'NEED TO BE DONE'
                },
                {
                    id: 3,
                    title: 'Item C',
                    status: 'BEING DONE'
                },
                {
                    id: 4,
                    title: 'Item D',
                    status: 'HAS BEEN DONE'
                },
                {
                    id: 5,
                    title: 'Item E',
                    status: 'NEED TO BE DONE'
                },
                {
                    id: 6,
                    title: 'Item F',
                    status: 'BEING DONE'
                },
                {
                    id: 7,
                    title: 'Item G',
                    status: 'HAS BEEN DONE'
                },
                {
                    id: 8,
                    title: 'Item H',
                    status: 'NEED TO BE DONE'
                },
                {
                    id: 9,
                    title: 'Item I',
                    status: 'BEING DONE'
                }
            ]
        }
    },
    computed:{
        needToBeDone(){
            return this.tasks.filter(x => x.status == "NEED TO BE DONE")
        },
        beingDone(){
            return this.tasks.filter(x => x.status == "BEING DONE")
        },
        hasBeenDone(){
            return this.tasks.filter(x => x.status == "HAS BEEN DONE")
        }
    }
}
</script>

<style scoped>
.container{
    margin: 30px 0;
}
.task-zone{
    display: flex;
    justify-content: space-around;
}
.drop-zone{
    border: 1px solid black;
    width: 100%;
    height: 400px;
    margin: 0 30px;
    border-radius: 20px;
    padding: 10px 0;
    transition: .3s;
    background-color:white;
}
.drop-zone:hover{
    transform: rotate(5deg);
}
.drag-el{
    border: 1px solid black;
    width: 200px;
    height: 40px;
    margin: 5px auto;
    padding-top: 15px;
    border-radius: 10px;
    transition: .3s;
    background-color:white;
}
.drag-el:hover{
    border-radius: 30px;
    transition: .3s;
    transform: scale(1.2) rotate(-5deg);
}
</style>