<template>
  <div class="timeline">
    <ul>
        <li v-for="tweet in tweets">
              {{ tweet }}
            </li>

      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      tweets: ['tweet 1', 'tweet 2', 'tweet 3']
    }
  }
}
</script>
