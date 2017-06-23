<template>
  <div class="timeline">
    <feed :tweets="tweets"/>
  </div>
</template>

<script>
import Feed from './Feed'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)

export default {
  name: 'timeline',
  data () {
    return {
      tweets: []
    }
  },
  components: { Feed },
  created () {
    this.fetchTweets()
  },
  methods: {
    fetchTweets: function () {
      this.$http.get('http://localhost:8080/list').then(response => {
        // get body data
        this.tweets = response.body
        console.log(response.body)
      }, response => {
        // error callback
      })
    }
  }
}
</script>

<style scoped>
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: block;
    margin: 0 10px;
  }
</style>
