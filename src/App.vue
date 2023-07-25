<template>
    <my-header>
        <div class="search">
            <my-input
                placeholder="Search"
                v-model="searchQuery"
            />
        </div>
    </my-header>
    <div class="posts">
        <div class="buttons-wrapper">
            <my-button @click="showDialog" text="Create post">Create post</my-button>
            <my-select
                v-model="selectedSort"
                :options="sortOptions"
            />
        </div>
        
        <my-dialog v-model:show="dialogVisible">
            <post-form @create="createPost" />
        </my-dialog>

        <loading v-model:active="isLoading"
                 class="vl-parent"
                 :can-cancel="true"
                 :on-cancel="onCancel"
                 :color="color"
                 :width="20"
                 :is-full-page="fullPage"/>

        <post-list 
            :posts="sortedAndSearch"
            @remove="removePost"
        />
    </div>
</template>

<script>
import MyHeader from '@/components/MyHeader';
import PostList from '@/components/PostList';
import PostForm from '@/components/PostForm';
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/css/index.css';
import axios from 'axios';

export default {
    components: {
    PostList,
    PostForm,
    Loading,
    MyHeader
},
    data() {
        return {
            posts: [],
            dialogVisible: false,
            isLoading: false,
            fullPage: false,
            color: '#007bff',
            selectedSort: '',
            searchQuery: '',
            sortOptions: [
                {value: 'title'},
                {value: 'body'}
            ]
        }
    },
    methods: {
        createPost(post) {
            this.posts.unshift(post)
            this.dialogVisible = false
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog() {
            this.dialogVisible = true
        },
        async fetchPosts() {
            this.isLoading = true;
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
                this.posts = response.data
                this.isLoading = false
            } catch (error) {
                alert('Something happend')
            }
        }
    },
    computed: {
        sortedPosts() {
            return [...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
        },
        sortedAndSearch() {
            return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
        }
    },
    mounted() {
        this.fetchPosts()
    }
}
</script>

<style lang="scss">
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'montserrat';
    }

    .vl-parent {
        position: relative;
    }

    .posts {
        display: grid;
        gap: 1rem;
        grid-template-columns: 1fr;
        max-width: 500px;
        margin: 0 auto;
        margin-top: 1rem;
    }

    .buttons-wrapper {
        display: flex;
        justify-content: space-between;
        margin: 0 1rem;
    }

    .search {
        border-radius: .5rem;
        max-width: 500px;
    }
</style>