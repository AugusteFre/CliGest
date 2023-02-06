<template>
  <q-page padding>
    <h3>Liste des clients</h3>

    <q-list
      class="rounded-borders"
      bordered
      separator
    >
      <client v-for="client in clients"
             :key="client.id"
             :client="client">
      </client>
    </q-list>
  </q-page>
</template>

<script>

import Client from 'components/Client'
import { mapActions } from 'vuex'

export default {
  name: 'ClientPage',
  components: { Client },

  computed: {
    clients () {
      return this.$store.getters['clients/getClients']
    }
  },
  methods: {
    ...mapActions('clients', ['getClientsApi'])
  },
  mounted () {
    this.getClientsApi()
  }
}
</script>
