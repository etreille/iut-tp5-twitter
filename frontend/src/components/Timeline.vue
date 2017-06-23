<template>
  <div class="timeline">
    <feed :tweets="tweets" :loading="loading" @retweeted="retweet"/>
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
      tweets: [],
      loading: true
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
        console.log(this.loading)
        this.tweets = response.body
        this.loading = false
        console.log(response.body)
        console.log(this.loading)
      }, response => {
        // error callback
      })
    },
    retweet: function (tweetId) {
      for (var i = 0; i < this.tweets.length; i++) {
        if (this.tweets[i].id === tweetId) {
          this.tweets[i].retweeters.push({handle: 'bob'})
        }
      }
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
