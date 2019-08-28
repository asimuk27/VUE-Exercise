<template>
  <div class="container" id="app">
  
    <UserSelection v-on:userChanged="userChanged"></UserSelection>
    <Postslist v-bind:source="source"></Postslist>

  </div>
</template>

<script>
import Postslist from './components/Postslist'
import UserSelection from './components/UserSelection'

export default {
  name: 'app',
  components: {
    Postslist,
    UserSelection
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    userChanged: function (source) {
      this.source = source;
    }
  }
}
</script>

<style>
  #app {
    padding-top: 20px
  }
</style>
