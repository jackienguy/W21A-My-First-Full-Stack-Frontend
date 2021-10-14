<template>
  <div>
      <!-- Post input box -->
    <div>
        <textarea 
            v-model="content" 
            placeholder="Post here"
            rows="6"
            cols="40"
            counter: maxlength="200"
            background-color="grey lighten-1"
        ></textarea>
        <button @click="createPost">Post</button>
    </div>
    <UserPost/>
  </div>
</template>

<script>
import axios from 'axios'
import UserPost from "./UserPost.vue"

    export default {
        name: "PostBox",
        components: {
            UserPost
        },
        data() {
            return {
                username: '',
                content: ''
            }
            
        },methods: {
            createPost(){
                axios.request({
                    url: "http://127.0.0.1:5000/api/blog",
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        content: this.conent
                    }
                }).then((response)=>{
                    console.log(response.data.content);
                    this.content = ''
                }).catch((err)=>{
                    console.error(err);
                })
            },
          
        }
    }
</script>


 