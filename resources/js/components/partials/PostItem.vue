<template>
  <article>
    <h4>{{post.title}}</h4>
    <p>{{truncatedText}}</p>
    <p class="date">{{formatDate}}</p>
    <p v-if="post.category" class="category">{{post.category.name}}</p>
    <p v-if="post.tags">
      <span v-for="tag in post.tags" :key="tag.id" class="tag">
        {{tag.name}}
      </span>
    </p>
  </article>
</template>

<script>
export default {
    name: 'PostItem',
    props:{
      'post' : Object,
    },

    computed:{
      truncatedText(){
        return this.post.title.substr(0,50) + '...';
      },

      formatDate(){
        const d = new Date(this.post.created_at);
        let date = d.getDate();
        if(date < 10) date = '0' + date;
        let month = d.getMonth();
        if(month < 10) month = '0' + month;
        let year = d.getFullYear();
        return `${date}/${month}/${year}`;
      }
    }
}
</script>

<style lang="scss" scoped>

article{
  margin: 30px 0;
  p{
    padding: 7px 0;
  }
  .date{
    font-style: italic;
  }
  .category{
    font-weight: bold;
    color: rgb(150, 10, 64);
  }
  .tag{
    padding: 2px 5px;
    margin-right: 10px;
    background-color:darkcyan;
    color: white;
    border-radius: 5px;
  }
}

</style>