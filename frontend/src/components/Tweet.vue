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
          <icon name="retweet"/> {{tweet.retweeters.length}}
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
  props: ['tweet'],
  components: { Icon },
  created () {
    moment.locale('fr')
  },
  methods: {
    moment: function (date) {
      return moment(date)
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
