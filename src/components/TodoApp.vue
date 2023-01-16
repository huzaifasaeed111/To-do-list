<template>
    <div class="container">
        <h2 class="text-center mt-5">My Todo App</h2>
        <div class="d-flex">
            <input type="text" v-model="task" placeholder="Enter Text" class="form-control">
            <button class="btn btn-warning rounded-0" @click="submitTask">Submit</button>
        </div>

        <table class="table mt-4">
            <thead>
              <tr>
                <th scope="col">Task</th>
                <th scope="col">Status</th>
                <th scope="col" class="text-center">#</th>
                <th scope="col" class="text-center">#</th>
              </tr>
            </thead>
            <tbody v-for="(task,index) in tasks" :key="index">
              <tr>
                <th>{{task.name}}</th>
                <td>{{task.status}}</td>
                <td>
                   <div class="text-center" @click="editTask(index)">
                     <span class="fa fa-pen"></span>
                   </div>
                </td>
                <td>
                    <div class="text-center" @click="deleteTask(index)">
                     <span class="fa fa-trash"></span>
                    </div>
                </td>
              </tr>
            </tbody>
          </table>

    </div>
</template>

<script>
   export default{
      name: 'TodoApp',
      data(){
        return{
            task:'',
            editedTask: null,
            tasks:[
                {
                    name: 'Ecommerce Task',
                    status: 'To-do'
                },
                {
                    name: 'Amazon Task',
                    status: 'In-Progress'
                }
            ]
        }
      },

      methods:{
        submitTask(){
            if(this.task.length === 0) return ;
            this.tasks.push({
                name: this.task,
                status: 'To-do',
            })
        },

        deleteTask(index){
            this.tasks.splice(index, 1);
        },

        editTask(index){
            this.task=this.tasks[index].name;
            this.editedTask = index;
        }
      }
   }
</script>

<style>
    
</style>