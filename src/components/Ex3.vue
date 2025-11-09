<script>
    import axios from 'axios'
    import blogPost from './subcomponents/BlogPost2.vue'
    
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        components: { blogPost },
        created() { 
            axios.get('http://localhost/is216/REST/blog/getPosts.php')
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        },
        methods: {
                deletePost(id) {
                    console.log("ID: " + id)
                    let idx = 0
                    for (let post of this.posts) {
                        if (post.id == id) {
                            this.posts.splice(idx,1) // remove this element
                            console.log(this.posts)
                            break
                        }
                        idx++
                    }
                    let url = 'http://localhost/is216/REST/blog/deletePost.php'
                    axios.get(url, { params: { id: id }
                    })
                    .then(response => {
                        console.log(response.data)
                        this.showStatus = true
                        this.status = response.data
                    })
                    .catch(error => {
                        this.showStatus = true
                        this.status = 'There was an error: ' + error.message 
                    })  

                }
        }
    }
</script>

<template>
    <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <blog-post v-for="post in posts" v-bind:key="post.id" v-bind:id="post.id" 
        v-bind:entry="post.entry" v-bind:mood="post.mood" v-bind:subject="post.subject">
        <button class="btn btn-primary" 
            v-on:click="deletePost(post.id)">Delete</button>
    </blog-post> 

</template>

