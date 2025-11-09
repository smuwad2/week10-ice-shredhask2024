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
            <slot></slot>
            <br />
        </div>
    </div>

</template>