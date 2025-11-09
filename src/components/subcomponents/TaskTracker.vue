<script>
    export default { 
        data() {
            return {
                show: false,
                desc: '',
                deadline: '',
                taskList: []
            }
        },
        props: ['task', 'idx'],
        methods: {
            add() {
                this.taskList.push( { 'desc': this.desc, 'deadline': this.deadline } )
                this.desc = ''
                this.deadline = ''
            },
            deleteTask(idx) {
                this.taskList.splice(idx,1)
            }
        }
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
    <div class="card" style="width: 18rem;display:inline-block;">
        <div class="card-body">
            <h5 class="card-title">Deadline: {{task.deadline}}</h5>
            <hr>
            <p class="card-text">{{task.desc}}</p>
            <button type="button" v-on:click="$emit('delete', idx)" class="btn btn-primary">Done</button>
        </div>
    </div>
</template>