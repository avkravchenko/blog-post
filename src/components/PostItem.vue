<template>
    <div class="post">
        <div>
            <div class="post-title"><strong>Post title: {{ post.title }}</strong></div>
            <div class="post-body">Post body: {{ post.body }}</div>
        </div>
        <div>
            <my-button @click="$emit('remove', post)">Remove</my-button>
        </div>
    </div>
</template>

<script>

    export default {
        props: {
            post: {
                type: Object,
                requiered: true
            }
        }
    }
</script>

<style lang="scss" scoped>
   .post {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        padding: 1rem;
        background-color: #fff;
        filter: drop-shadow(2px 2px 2px rgb(176, 176, 176));
        border-radius: 1rem;
        margin: 1rem;

        .post-title {
            margin-bottom: 1rem;
        }
    }
</style>