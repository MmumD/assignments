<!-- SOMETHING -->
<template>
    <div class="post">
        <div><strong>Name:</strong>{{post.title}}</div>
        <div><strong>Description:</strong>{{post.body}}</div>
    </div> 
</template>

<!-- SCRIPT -->
<script>
export default{
    props:{
        post:{
            type: Object,
            required: true,
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