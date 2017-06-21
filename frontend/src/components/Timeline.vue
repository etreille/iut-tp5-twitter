<template>
  <div class="timeline">
    <ul>
      <li v-for="tweet in tweets">
        {{ tweet.auteur }} : {{tweet.contenu}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      tweets: [
        {auteur: 'Jean', contenu: 'Hello Tweeter!'},
        {auteur: 'Bob', contenu: 'tweet 3'}
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
