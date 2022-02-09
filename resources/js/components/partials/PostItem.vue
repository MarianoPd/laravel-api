<template>
  <article>
    <h4>{{post.title}}</h4>
    <p>{{truncatedText}}</p>
    <p class="date">{{formatDate}}</p>

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
}

</style>