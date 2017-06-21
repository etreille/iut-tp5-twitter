<template>
  <div class="timeline">
    <ul>
      <li v-for="tweet in tweets">
        <tweet :tweet="tweet"/>
      </li>
    </ul>
  </div>
</template>

<script>
import Tweet from './Tweet'
import Vue from 'vue'
import Resource from 'vue-resource'
Vue.use(Resource)

export default {
  components: { Tweet },
  name: 'timeline',
  data () {
    return {
      tweets: [
        {author: 'Jean', content: 'Hello Tweeter!'},
        {author: 'Bob', content: 'tweet 3'}
      ]
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
