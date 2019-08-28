<template>
  <div class="sourceselection">
    <div>
      <div class="jumbotron">
        <h2><span class="glyphicon glyphicon-list-alt"></span>&nbsp;Users List</h2>
        <select class="form-control" v-on:change="userChanged">
          <option value="">Please select user ...</option>
          <option v-for="user in users" v-bind:value="user.id">{{user.name}}</option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'sourceselection',
  data () {
    return {
      users: [],
      user: ''
    }
  },
  methods: {
    userChanged: function(e) {
     for (var i=0; i<this.users.length; i++) {
       if (this.users[i].id == e.target.value) {
         this.user = this.users[i];
       }
     }
     this.$emit('userChanged', e.target.value);
    }
  },
  created: function () {
    this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        this.users = response.data;
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
