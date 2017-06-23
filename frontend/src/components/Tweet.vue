<template>
  <div class="tweet">
    {{ tweet.auteur }} : {{ tweet.contenu }}
  </div>
</template>

<script>
export default {
  name: 'hello',
  props: ['tweet']
}
</script>
