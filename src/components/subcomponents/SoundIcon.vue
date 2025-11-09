<script>
    export default { 
        props: ['level'],
        data() {
            return {
                soundEmojis: ['🔇', '🔈', '🔉', '🔊']
            }
        }
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
    <span>{{soundEmojis[level]}}</span>
</template>