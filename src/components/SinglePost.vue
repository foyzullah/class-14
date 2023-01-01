<script>

export default{
    name:'SinglePost',
    props:{
        post:{
            type: Object
        }
        
    },
    methods: {
        
    
        
    }
}


</script>

<template>
    
    <li class="flex items-center border justify-between border-blue-400 p-2 mb-2 text-center rounded h-full ">
        <h2 class="font-semibold mr-5">{{ post.title }}</h2>
        <div class="flex justify-between ">
            <button @click="$emit('delete-post', post)" class="border border-blue-400 font-semibold mr-2 px-2 py-1 rounded">Delete</button>
            <button @click="$emit('complete-task', post)" class="border border-blue-400 font-semibold px-2 py-1 rounded">Complete</button>
        </div>
    </li>
        
</template>