<!-- SOMETHING -->
<template>
    <div class="timeform">
        <form @submit.prevent>
            <input type="text" placeholder="Title" v-model="timeEvent.title">
            <input type="date" placeholder="date" v-model="timeEvent.date">
            <input type="text" placeholder="description" v-model="timeEvent.description">
            <button @click="createEvent">Add</button>
        </form>
    </div>
</template>

<!-- SCRIPT -->
<script>
export default{
    data(){
        return{
            timeEvent: {
                title: "",
                date: "",
                description: ""
            }
        }
    },
    methods:{
        createEvent(){
            if(this.timeEvent.title == "" || this.timeEvent.description == ""){
                return;
            }else{
                this.$emit('create', this.timeEvent);
                this.timeEvent = {
                    title: '',
                    date: '',
                    description: ''
                }
            }
        }
    }
}
</script>

<!-- STYLE -->
<style>
</style>