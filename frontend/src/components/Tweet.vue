<template>
  <div >
    <div>
      <strong>{{ tweet.auteur.prenom }} {{ tweet.auteur.nom }}</strong>
      <span class ="handle">@{{ tweet.auteur.handle }} - {{moment(tweet.date).fromNow()}}</span>
    </div>
    <div>
      {{ tweet.contenu }}
    </div>
    <div>
      <ul>
        <li class="button">
          <icon name="reply"/>
          <a @click="retweet(tweet.id)"><icon name="retweet"/></a> {{tweet.retweeters.length}}
          <icon name="heart"/>
          <icon name="envelope"/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
import moment from 'moment'

export default {
  name: 'hello',
  props: ['tweet', 'utilisateur'],
  components: { Icon },
  created () {
    moment.locale('fr')
  },
  methods: {
    moment: function (date) {
      return moment(date)
    },
    retweet: function (tweetId) {
      var formData = new FormData()
      formData.append('utilisateur', this.utilisateur)
      formData.append('tweet', tweetId)
      this.$http.post('http://localhost:8080/retweet', formData, {responseType: 'text'}).then(response => {
        this.$emit('retweeted', tweetId)
      })
    }
  }
}
</script>

<style scoped>
li.button {
 display: inline-block;
}

a {
 color: #42b983;
}

span.handle {
 color: gray;
}

</style>
