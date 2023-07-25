<template>
    <form @submit.prevent class="posts__post-form">
        <my-input 
            v-model="post.title"
            type="text" 
            placeholder="New title" />
        <my-input 
            v-model="post.body"
            type="text" 
            placeholder="New description" />
        <my-button
            class="posts__post-form__submit"
            @click="createPost">
            Add new post
        </my-button>
    </form>
</template>

<script>

    export default {
    data() {
        return {
            post: {
                title: "",
                body: "",
            }
        };
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit("create", this.post);
            this.post = {
                title: "",
                body: "",
            };
        }
    },
}
</script>

<style lang="scss" scoped>
    .posts__post-form {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        background-color: rgb(0, 128, 255);
        padding: 1rem;
        border-radius: 1rem;
        width: 100%;

        &__submit {
            align-self: flex-end;
        }
    }
</style>