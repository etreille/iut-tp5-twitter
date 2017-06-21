<template>
  <div class="tweet">
    {{ tweet.author }} : {{ tweet.content }}
  </div>
</template>

<script>
export default {
  name: 'hello',
  props: ['tweet']
}
</script>
