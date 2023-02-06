<template>
  <q-page padding>
    <h3>Liste des clients</h3>

    <q-list
      v-if="clients.length"
      class="rounded-borders"
      bordered
      separator
    >
      <client v-for="client in clients"
             :key="client.id"
             :client="client">
      </client>
    </q-list>
    <p v-else>Pas de clients ...</p>
  </q-page>
</template>

<script>

import Client from 'components/Client'
import { mapActions } from 'vuex'

export default {
  name: 'ClientPage',
  components: { Client },

  computed: {
    // récupère les clients par défaut
    clients () {
      return this.$store.getters['clients/getClients']
    }
  },
  methods: {
    // mappe l'action de récupérer des clients par API
    ...mapActions('clients', ['getClientsApi'])
  },
  // mounted est appelé quand le composant est ajouté
  mounted () {
    // récupère les clients générés par API
    this.getClientsApi()
  }
}
</script>
