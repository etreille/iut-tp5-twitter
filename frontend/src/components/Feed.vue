<template>
  <div class="feed">
    <div v-if="loading === true">
      <h2>Chargement des tweets</h2>
    </div>
    <div v-else>
      <ul>
        <li class="tweet" v-for="tweet in tweets">
          <tweet :tweet="tweet"/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Tweet from './Tweet'
export default {
  name: 'feed',
  props: ['tweets', 'loading'],
  components: { Tweet }
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

  li.tweet:first-child {
   border-top-width: 1px;
  }

  li.tweet {
   border-style: solid;
   border-width: 0 1px 1px 1px;
   border-color: gray;
   width: 500px;
   margin: auto;
  }
</style>
