<template>
  <div class="container">
     <h2 class="text-center mt-5">List</h2>
      <!--Input-->
      <div class="d-flex">
        <input v-model="task " type="text" placeholder="Enter text"  class="form-control" >
        <button @click="submitTask" class="btn btn-warning rounded-0">submit</button>
      </div>

      <!--task table-->
      <table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">status</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
      <th><span :class="{'finished': task.status == 'finished'}">{{task.name}}</span></th>
      <td style="width: 120px"><span @click="changeStatus(index)" class="pointer"
                                     :class="{'text-danger':task.status=='to-do',
                                               'text-warning':task.status=='in-progress',
                                               'text-success':task.status=='finished'}">
                 {{ firstCharUpper(task.status) }}</span></td>
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center"
        @click="deletTask(index)">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      task:'',
      tasks:[],
      editedTask:null,
      availableStatus: ['to-do' ,'in-progress','finished']
    }
  },
  methods:{
     submitTask(){
      if(this.task.length == 0) return;
      if(this.editedTask==null){
      this.tasks.push({
        name: this.task,
        status: 'to-do'
      });
      }
      else{
         this.tasks[this.editedTask].name = this.task;
         this.editedTask = null;
      }
      this.task = '';
     },
     deletTask(index){
       this.tasks.splice(index,1)
     },
     editTask(index){
       this.task = this.tasks[index].name;
       this.editedTask = index;
     },
     changeStatus(index){
      let newIndex = this.availableStatus.indexOf(this.tasks[index].status);
    if(++newIndex > 2) newIndex = 0;
    this.tasks[index].status = this.availableStatus[newIndex];
     },
     firstCharUpper(str){
         return str.charAt(0).toUpperCase() + str.slice(1);
     }
  
  } 
};
</script>
<style scoped>
.pointer {
  cursor:pointer;
}
 .finished{
   text-decoration: line-through;
 }
</style>


