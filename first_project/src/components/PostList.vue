<!-- SOMETHING -->
<template>
    <div>
        <h3>List of Guests</h3>
        <post-item
            v-for="post in posts" 
            v-bind:post="post"/> 
    </div>
    
</template>

<!-- SCRIPT -->
<script>
import PostItem from './PostItem.vue';
export default{
    components:{PostItem},
    props:{
        posts:{
            type: Array,
            required: true
        }
    }
}
</script>

<!-- STYLE -->
<style>
.post{
    padding: 15px;
    border: 1px solid teal;
    margin-top: 15px;
}
</style>