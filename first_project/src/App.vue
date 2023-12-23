<!-- SOMETHING -->
<template>
    <div class="app">
        <post-form @create="createPost"/>
        <post-list v-bind:posts="posts"/>
    </div>
</template>

<!-- SCRIPT -->
<script>
import PostForm from "./components/PostForm"
import PostList from "./components/PostList"
export default{
    components:{
        PostForm,
        PostList
    },
    data(){
        return{
            posts: [
                {id: 1, title: 'JS', body: "Unic"},
                {id: 2, title: 'HTML', body: "Program"},
                {id: 3, title: 'CSS', body: "Language"},
            ]
        }
    },
    methods:{
        createPost(post){
            this.posts.push(post);
        }
    }
}
</script>

<!-- STYLE -->
<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app{
    padding: 20px;
}
</style>