<script>
import SinglePost from './components/SinglePost.vue'
import CompleteTask from './components/CompleteTask.vue'
export default{
  components: { SinglePost,CompleteTask },
    name:'HomePage',
    data(){
      return{
        posts:[
          {
            id:1,
            title: 'Task-1',
            isTaskComplete: false
          },
          {
            id:2,
            title: 'Task-2',
            isTaskComplete: false
          },
          {
            id:3,
            title: 'Task-3',
            isTaskComplete: false
          }
        ],

        completeTasks:[]
      }
    },

    computed:{
      completeTask(post){
        return this.posts.filter(post=>post.isTaskComplete)
      }
    },
    methods:{
      addTask(){
        this.posts.push({
          id:this.posts.length+1,
          title: `Task ${this.posts.length+1}`,
          isTaskComplete: false
        })
      },

      handleDelete(post){
        this.posts= this.posts.filter(p=>p.id != post.id)
        
        // console.log('delete');
      },

      handleCompleteTask(post){
        // this.completeTasks =this.posts.filter(p=>p.id=post.id)[0]

        this.posts=this.posts.map(p=>{
          if(p.id===post.id){
            p.isTaskComplete=!p.isTaskComplete;
          }

          return p
        })
      }
    }
}


</script>
<template>
  <div class="container mx-auto mt-5">

    <button @click="addTask" class="border border-blue-400 font-semibold mr-2 mb-5 px-2 py-1 rounded">Add Task</button>
    <h2>All Tasks</h2>
    <ul class="h-full">
      <single-post 
      v-for="post in posts"
      :kay="post.id"
      :post="post"
      @delete-post="handleDelete"
      @complete-task="handleCompleteTask"

      />
    </ul>

  <br>

  <h2>Complete task</h2>
    <ul class="h-full">
        <complete-task 
        v-for="post in completeTask"
        :kay="post.id"
        :post="post"
        @delete-post="handleDelete"
        @complete-task="handleCompleteTask"
        />
      </ul>
  </div>
</template>
