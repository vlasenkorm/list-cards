<template>
  <v-app>
    <v-main>
      <PageList/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import PageList from './components/PageList.vue'

export default Vue.extend({
  name: 'App',

  components: {
    PageList
  },

  data: () => ({
    //
  })
})
</script>
