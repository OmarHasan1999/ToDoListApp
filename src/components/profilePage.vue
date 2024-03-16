<template lang="">
    <div class="main">
        <h3>Todo App</h3>
        <input v-model="task" type="text" placeholder="Enter task" @keyup.enter="addTask"/>
        <button @click="addTask">Submit</button>
        <table >
            <tr>
              <th>Task</th>
              <th>Status</th>
              <th>#</th>
              <th>#</th>
            </tr>
            <tr v-for="(item,index) in theTasks" :key="index">
              <td :style="{'text-decoration' : item.status === 'Finish' ? 'line-through' : 'none'}">
              {{ item.yourTask }}</td>
              <td @click="togglstatus(index)" :style="{'color' : item.status === 'Finish' ? 'green' : 'black'}">{{ item.status }}</td>
              <td @click="deleteTask(index)"><i class="fa-solid fa-trash"></i></td>
              <td @click="editTask(index)"><i class="fa-solid fa-pen"></i></td>
            </tr>
           
        </table>
    </div>
</template>




<script>
export default {
    data() {
        return {
            theTasks:[
                {
                    yourTask: "steal bananas from the supermarket",
                    status:"To-do"
                    
                },
                {
                    yourTask: "Eat 1kg in 1 hour",
                    status:"Finish",
                    
                },
                {
                    yourTask: "create youtube video",
                    status:"To-do"
                    
                }
            ],
            task:"",
            update : null,
            status : "To-do",
            
        }
    },
   methods: {
    addTask(){
        if(this.task === "") return;

        if(this.update === null)
        this.theTasks.push({
            yourTask : this.task,
            status : "To-do"
        })
        else(this.theTasks[this.update].yourTask = this.task)
        this.task= ""
    },

    deleteTask(index){
       this.theTasks.splice(index, 1)
    },
    editTask(index){
        this.task = this.theTasks[index].yourTask;
        this.update = index
    },
    togglstatus(index){
        if(this.theTasks[index].status === "To-do"){
            this.theTasks[index].status = "Finish"
        }else(
            this.theTasks[index].status = "To-do"
        )
    }
    
   },
}
</script>




<style lang="css">
    *{
        margin: 0%;
        padding: 0%;
        user-select: none;
    }
    body{
        box-sizing: border-box;
        width: 100%;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        display: flex;
        justify-content: center;
    }
    .main{
        margin-top: 12vh;
        flex-direction: column;

    }
    .main h3{
        color: rgba(0, 0, 0, 0.759);
        font-size: 30px;
        font-weight: 700;
        margin-left: 12vh;
    }
    .main input{
      width: 65vh;
      height: 5vh;
      color: rgba(0, 0, 0, 0.395);
      margin-top: 5vh;
      margin-left: -10vh;
      padding-left: 2vh;
      border: 1px solid rgba(0, 0, 0, 0.137);
      border-radius: 3px;
      font-size: 14px;
    }
    .main button{
      padding: 1.3vh 3vh;
      background-color: rgba(255, 166, 0, 0.752);
      border: 1px solid rgba(0, 0, 0, 0);
      border-radius: 2px;
      margin-left: -0.3vh;
      cursor: pointer;
    }
    table{
        margin-top: 7vh;
        border-collapse: collapse;
        width: 80vh;
        height: 35vh;
        margin-left: -9.7vh;

    }
    table, td, th{
        border: 1.6px solid rgba(0, 0, 0, 0.068);

    }
    td{
        color: rgba(0, 0, 0, 0.748);
        padding: 2vh;
        cursor: pointer;
        text-align: center;
    }
    th{
    padding: 2vh;
    }

    @media only screen and (max-width: 414px){
        *{
        margin: 0%;
        padding: 0%;
        user-select: none;
    }
    body{
        box-sizing: border-box;
        width: 100%;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        display: flex;
        justify-content: center;
    }
    .main{
        margin-top: 12vh;
        flex-direction: column;

    }
    .main h3{
        color: rgba(0, 0, 0, 0.759);
        font-size: 24px;
        font-weight: 700;
        margin-left: 16vh;
    }
    .main input{
      width: 40vh;
      height: 5vh;
      color: rgba(0, 0, 0, 0.395);
      margin-top: 5vh;
      margin-left: 7vh;
      padding-left: 2vh;
      border: 1px solid rgba(0, 0, 0, 0.137);
      border-radius: 3px;
      font-size: 14px;
    }
    .main button{
      padding: 1.1vh 2vh;
      background-color: rgba(255, 166, 0, 0.752);
      border: 1px solid rgba(0, 0, 0, 0);
      border-radius: 2px;
      cursor: pointer;
    }
    table{
        margin-top: 7vh;
        border-collapse: collapse;
        width: 65vh;
        height: 40vh;
        margin-left: 2vh;

    }
    table, td, th{
        border: 1.6px solid rgba(0, 0, 0, 0.068);

    }
    td{
        color: rgba(0, 0, 0, 0.748);
        padding: 2vh;
        cursor: pointer;
        text-align: center;
    }
    th{
    padding: 2vh;
    }
    }
</style>