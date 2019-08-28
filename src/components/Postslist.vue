<template>
  <div class="newslist">
    <div class="container">
      <ul class="media-list">
        <li class="media" v-for="article in posts">
          <div class="media-body">
            <h4 class="media-heading">{{article.title}}</h4>
            <p>{{article.body}}</p>
          </div>
        </li>
      </ul>

    </div>
  </div>
</template>

<script>
export default {
  name: 'postslist',
  props: ['source'],
  data () {
    return {
      posts: []
    }
  },
  methods: {
    updateSource: function (source) {
      this.$http.get('https://jsonplaceholder.typicode.com/posts?userId=' + source )
       .then(response => {
         this.posts = response.data;
       });   
    }
  },
  created: function () {
    this.updateSource(this.source);
  },
  watch: {
    source: function (val) {
      this.updateSource(val);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .media-object {
    width: 128px;
    padding: 10px;
  }
  .media {
    border-top: 1px solid lightgray;
    padding-top: 20px;
  }
</style>
