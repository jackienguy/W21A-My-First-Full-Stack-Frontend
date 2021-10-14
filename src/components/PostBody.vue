<template>
    <div>
        <button @click="editPost">Edit</button>
        <button @click="deletePost">Delete</button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "PostBody",
    props: {
        blogid: Number,
        content: String,
        username: String
    },
    methods: {
        editPost() {
            axios.request({
                url: "http://myfullstack.ml/api/blog",
                method: "PATCH",
                headers: {
                    "Content-Type": "application/json"
                },
                data: {
                    blogid: this.blogid,
                    content: this.content
                }
            }).then((response)=>{
                console.log(response);
            }).catch((err)=>{
                console.error(err);
            })
        },
        deletePost(){
            axios.request({
                url: "http://myfullstack.ml/api/blog",
                method: "DELETE",
                headers: {
                    "Content-Type": "application/json"
                },
                data: {
                    blogid: this.blogid
                }
            }).then((response)=>{
                console.log(response);
            }).catch((err)=>{
                console.error(err);
            })
        }
    }
}
</script>
