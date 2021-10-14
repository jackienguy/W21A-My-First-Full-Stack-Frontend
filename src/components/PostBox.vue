<template>
  <div>
      <!-- User new tweet input box -->
      <v-container class="pb-10 ml-6">
        <v-row>
                <v-col
                class="ml-6"
                cols="15"
                md="10"
                >
                <v-textarea 
                    v-model="content" 
                    placeholder="Post here"
                    counter: maxlength="200"
                    background-color="grey lighten-1"
                ></v-textarea>
                </v-col>
            </v-row>
            <v-btn  
            class="ml-6" 
            @click="createPost"
            >
              Post
            </v-btn>
      </v-container>
      <v-divider></v-divider> 
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
                }
        }
    }
</script>


 