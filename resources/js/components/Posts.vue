<template>
  <main>
      <div v-if="posts" class="container">
          <div class="title">
              <h1>Posts</h1>
          </div>
          <PostItem 
            v-for="post in posts"
            :key="post.id"
            :post = post
          />

          <div class="pagination">
              <button
                @click="getApi(pagination.current - 1)"
                :disabled = "pagination.current === 1"
              ><<</button>

              <button
                v-for="i in pagination.last"
                :key="i"
                @click="getApi(i)"
                :disabled = "pagination.current === i"
              >
                {{i}}
              </button>

              <button
                @click="getApi(pagination.current + 1)"
                :disabled = "pagination.current === pagination.last"
              >>></button>
          </div>
      </div>
      <div v-else class="container">
          <Loading/>
      </div>
  </main>
</template>

<script>
import PostItem from './partials/PostItem.vue';
import Loading from './partials/Loading.vue';

export default {
    name: 'Posts',

    components:{
        PostItem,
        Loading,
    },

    data(){
        return{
            apiUrl: 'http://127.0.0.1:8000/api/posts?page=',
            posts: null,
            pagination: {},
        }
    },

    mounted(){
        this.getApi();
    },

    methods:{
        getApi(page = 1){
            axios.get(this.apiUrl + page)
                .then(res => {
                    this.posts = null;
                    this.posts = res.data.data;
                    this.pagination = {
                        current: res.data.current_page,
                        last: res.data.last_page,
                    }
                    console.log(this.pagination);
                    console.log(this.posts);
                })
        }
    }
}
</script>

<style lang="scss" scoped>

    main{
        padding-bottom: 70px;
        .title{
            width: 100%;
            text-align: center;
            padding: 20px 0;
            color: sandybrown;
        }

        .pagination{
            text-align: center;
            button{
                cursor: pointer;
                padding: 5px;
            }
        }
    }

</style>