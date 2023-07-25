<template>
    <div v-if="posts.length > 0">
        <p class="feed">Feed</p>
        <transition-group name="post-list">
            <post-item 
            v-for="post in posts"
            :post="post" 
            :key="post.id"
            @remove="$emit('remove', post)"
            />
        </transition-group>
    </div>
    <div v-else>
        <p class="feed">Feed is empty</p>
    </div>

</template>

<script>
import PostItem from './PostItem.vue';
    export default {
        components: {
            PostItem
        },
        props: {
            posts: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style lang="scss" scoped>
.feed {
    text-align: center  ;
}
.post-list-move,
.post-list-enter-active,
.post-list-leave-active {
  transition: all 0.5s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>