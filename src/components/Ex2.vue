<script>
   import blogPost from './subcomponents/BlogPost.vue'
   import axios from 'axios'

    export default {
        
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        // component registration
        // for simplicity, we will use the following syntax
        components: { blogPost },
        // this is a more proper way to register
        // components: { 'blog-post' : blogPost },
       
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
        }
    }
</script>

<template>
    <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <blog-post v-for="post in posts" v-bind:id="post.id" 
        v-bind:entry="post.entry" v-bind:mood="post.mood" 
        v-bind:subject="post.subject">
    </blog-post> 

</template>

