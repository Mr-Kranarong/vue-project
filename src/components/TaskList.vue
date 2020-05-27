<template>
    <div class="container">

        <div class="add-task">
            <input id="new-task" type="text" v-model="newTask" maxlength="8"><br>
            <button id="add-button" type="button" @click="addTask(newTask)">Add New Task</button>
        </div>

        <div class="task-zone">
            <div class="drop-zone" @drop="onDrop($event,'NEED TO BE DONE')" @dragenter.prevent @dragover.prevent>
                <h1>What Need To Be Done</h1>
                <div class="drag-el" draggable @dragstart="onStart($event,task)" v-for="task in needToBeDone" :key="task.id">
                    <span v-if="editTask != task.id">{{task.title}}</span>
                    <input v-else class="edit-task" type="text" v-model="task.title">
                    <br>
                    <button v-if="editTask != task.id" type="button" @click="onEdit(task)">Edit</button>
                    <button v-else type="button" @click="onSave(task)">Save</button>
                    <button type="button" @click="onDelete(task.id)">Delete</button>
                </div>
            </div>
            <div class="drop-zone" @drop="onDrop($event,'BEING DONE')" @dragenter.prevent @dragover.prevent>
                <h1>Das Kapital</h1>
                <div class="drag-el" draggable @dragstart="onStart($event,task)" v-for="task in beingDone" :key="task.id">
                    <span v-if="editTask != task.id">{{task.title}}</span>
                    <input v-else class="edit-task" type="text" v-model="task.title">
                    <br>
                    <button v-if="editTask != task.id" type="button" @click="onEdit(task)">Edit</button>
                    <button v-else type="button" @click="onSave(task)">Save</button>
                    <button type="button" @click="onDelete(task.id)">Delete</button>
                </div>
            </div>
            <div class="drop-zone" @drop="onDrop($event,'HAS BEEN DONE')" @dragenter.prevent @dragover.prevent>
                <h1>What Has Been Done</h1>
                <div class="drag-el" draggable @dragstart="onStart($event,task)" v-for="task in hasBeenDone" :key="task.id">
                    <span v-if="editTask != task.id">{{task.title}}</span>
                    <input v-else class="edit-task" type="text" v-model="task.title">
                    <br>
                    <button v-if="editTask != task.id" type="button" @click="onEdit(task)">Edit</button>
                    <button v-else type="button" @click="onSave(task)">Save</button>
                    <button type="button" @click="onDelete(task.id)">Delete</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    async created(){
        let {data} = await axios.get('http://localhost:3000/tasks')
        console.log("axios ::: ", data)
        this.tasks = data;
    },
    data(){
        return{
            tasks:[],
            newTask: "",
            editTask:""
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
    },
    methods:{
        onStart(e, task){
            e.dataTransfer.dropEffect = "move"
            e.dataTransfer.effectAllowed = "move"
            e.dataTransfer.setData('taskId',task.id)
        },
        onDrop(e, newStatus){
            let taskid = e.dataTransfer.getData('taskId')
            let found = this.tasks.find(task => task.id == taskid)
            found.status = newStatus
        },
        addTask(newTask){
            let newId = this.tasks.length+1
            let str = newTask
            this.tasks.push({id:newId,title:"Item "+str.toUpperCase(),status:'NEED TO BE DONE'})
            this.newTask = ""
        },
        onEdit(task){
            this.editTask = task.id
        },
        onSave(updateTask){
            let thisTask = this.tasks.find(task=>task.id == updateTask.id)
            thisTask.title = updateTask.title
            this.editTask = null
        },
        onDelete(deleteTaskId){
            this.tasks = this.tasks.filter(task=>task.id != deleteTaskId)
        }
    }
}
</script>

<style scoped>
.container,.add-task{
    margin: 30px 0;
}
.task-zone{
    display: flex;
    justify-content: space-around;
}
.drop-zone{
    border: 1px solid black;
    width: 100%;
    min-height: 400px;
    margin: 0 30px;
    border-radius: 20px;
    padding: 15px 0;
    transition: .3s;
    background-color:white;
}
.drop-zone:hover{
    transition: .3s;
    transform: rotate(5deg);
}
.drag-el{
    border: 1px solid black;
    width: 200px;
    margin: 5px auto;
    padding: 10px;
    border-radius: 10px;
    transition: .3s;
    background-color:white;
}
.drag-el:hover{
    border-radius: 30px;
    transition: .3s;
    transform: scale(1.2) rotate(-5deg);
}
button{
    display: inline-block;
    background-color: white;
    border-radius: 10px;
    outline: none;
    border: 1px solid black;
    width: 40%;
}
#add-button{
    width: auto;
}
input[type="text"]{
    outline: none;
    border: 1px solid black;
    border-radius: 10px;
    padding: 5px;
}
</style>