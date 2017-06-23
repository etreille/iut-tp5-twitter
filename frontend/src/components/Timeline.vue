<template>
  <div class="timeline">
    <h1> {{ this.utilisateur ? 'Bonjour ' + this.utilisateur +' ! ' : 'Identifiez-vous !' }} </h1>
    <utilisateurs :utilisateurs="utilisateurs"  @userChanged="onChange"/>
    <feed :tweets="tweets" :loading="loading" :utilisateur="utilisateur" @retweeted="retweet"/>
  </div>
</template>

<script>
import Feed from './Feed'
import Utilisateurs from './Utilisateurs'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)

export default {
  name: 'timeline',
  props: ['utilisateur'],
  data () {
    return {
      tweets: [],
      loading: true,
      utilisateurs: []
    }
  },
  components: { Feed, Utilisateurs },
  created () {
    this.fetchTweets()
    this.fetchUtilisateurs()
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
          this.tweets[i].retweeters.push({handle: this.utilisateur})
        }
      }
    },
    onChange: function (handle) {
      this.utilisateur = handle
    },
    fetchUtilisateurs: function () {
      this.$http.get('http://localhost:8080/utilisateurs').then(response => {
        this.utilisateurs = response.body
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
