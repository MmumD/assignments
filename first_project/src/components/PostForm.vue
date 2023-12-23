<!-- SOMETHING -->
<template>
    <form @submit.prevent>
        <h4>Create Post</h4>
        <input v-model="post.title" class="inputs" type="text" placeholder="Title">
        <input v-model="post.body" class="inputs" type="text" placeholder="Description">
        <button class="add" @click="createPost">Add</button>
    </form>
</template>

<!-- SCRIPT -->
<script>
export default{
    data(){
        return{
            post:{
                title:"",
                body:""
            }
        }
    },
    methods: {
        createPost(){
            this.post.id = Date.now();
            if(this.post.title == "" || this.post.body == ""){
                return;
            }else{
                this.$emit('create', this.post);
                this.post = {
                    title: '',
                    body: ''
                }
            }
        }
    }    
}
</script>

<!-- STYLE -->
<style>
.inputs{
    width: 100%;
    border: 1px solid teal;
    padding: 10px 15px;
    margin-top: 15px;
}
form{
    display: flex;
    flex-direction: column;
}
.add{
    padding: 10px 20px;
    margin-top: 15px;
    border: 1px solid teal;
    color: teal;
    border-radius: 5px;
    align-self: flex-end;
    cursor: pointer;
}
</style>