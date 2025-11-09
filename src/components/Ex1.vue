<script>
 // TODO: Import the SoundIcon component 
    import soundIcon from './subcomponents/SoundIcon.vue'
    export default { 
        data() {
            return {
                soundLevel: 0
            }
        },
        components: {
            soundIcon,
        }
    }
</script>

<template>

   Sound level
    <input type="number" min="0" max="3" v-model="soundLevel"> 
    <!-- TODO: Add Code Here to make use of the SoundIcon component -->
    <sound-icon v-bind:level="soundLevel"></sound-icon>

</template>

