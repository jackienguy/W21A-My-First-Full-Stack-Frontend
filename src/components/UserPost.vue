<template>
    <div>
        <PostBody
        v-for="post in posts"
        :key="post.blogid"
        :content="post.content"
        :username="post.username"
        />
    </div>
</template>

<script>
import axios from 'axios';
import PostBody from "./PostBody.vue";

    export default {
        name: "UserPost",
        components: {
            PostBody
        },
        data() {
            return {
                posts: []
            }
        },
        mounted(){
            this.getPost()
        },
        methods: {
            getPost(){
                axios.request({
                    url: "http://127.0.0.1:5000/api/blog",
                    method: "GET",
                    params: {
                        username: this.posts.username
                    }
                }).then((response) =>{
                    console.log(response.data);
                    this.posts = response.data
                }).catch((err)=>{
                    console.error(err);
                })
            }
        }
    }
</script>