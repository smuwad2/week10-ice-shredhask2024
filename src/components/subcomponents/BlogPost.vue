<script setup>
    // Composition API example
    // const props = defineProps({ 
    //     id: String,
    //     subject: String,
    //     entry: String,
    //     mood: String
    // })
    // import angry from '/assets/angry.png' 
    // import happy from '/assets/happy.png'
    // import sad from '/assets/sad.png'

    // console.log(props.mood)
</script>

<script>
    export default {
        props: ['id', 'subject', 'entry', 'mood'],
        computed: {
            feel() {
                return "/assets/" + this.mood.toLowerCase() + ".png"
            }
        }
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
    <div class="card mx-auto" style="width: 24rem;">
        <img :src="feel" class="card-img-top" alt="Image cap">  
        <div class="card-body">
            <h5 class="card-title"> Blog {{ id }} Subject {{ subject }} </h5>
            <p class="card-text"> {{ entry }} </p>
            <hr size="10" noshade>
            <br />
        </div>
    </div>

</template>