<template>
  <div >
    <div>
      <strong>{{ tweet.auteur.prenom }} {{ tweet.auteur.nom }}</strong>
      <span class ="handle">@{{ tweet.auteur.handle }}</span>
    </div>
    <div>
      {{ tweet.contenu }}
    </div>
    <div>
      <ul>
        <li class="button">
          <icon name="reply"/>
          <icon name="retweet"/>
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

export default {
  name: 'hello',
  props: ['tweet'],
  components: { Icon }
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
