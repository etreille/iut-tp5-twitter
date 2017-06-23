<template>
  <select @change="onChange($event.target.value)">
    <option value="">Choisissez un utilisateur ...</option>
    <option v-for="utilisateur in utilisateurs" :value="utilisateur.handle">
      {{ utilisateur.prenom }} {{ utilisateur.nom }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'utilisateurs',
  props: [ 'utilisateurs' ],
  methods: {
    onChange: function (handle) {
      this.$emit('userChanged', handle)
    }
  }
}
</script>
