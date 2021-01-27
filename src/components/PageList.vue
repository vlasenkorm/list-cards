<template>
  <v-app>
    <v-container fluid grid-list-xl>
      <v-row justify="center">
        <h1>Title Page</h1>
      </v-row>

      <v-row class="filter">
        <v-col cols="2">
          <h2>Filter:</h2>
        </v-col>
        <v-col >
          <v-btn @click="handlerFilterBtn('all')" :input-value="this.currentFilter === 'all'">All</v-btn>
          <v-btn @click="handlerFilterBtn('Baskets')" :input-value="this.currentFilter === 'Baskets'">Baskets</v-btn>
          <v-btn @click="handlerFilterBtn('Bots')" :input-value="this.currentFilter === 'Bots'">Bots</v-btn>
          <v-btn>Coming soon</v-btn>
        </v-col>
      </v-row>

      <v-layout wrap justify-space-around>

        <div v-for="node in arrayData()" :key="node.num">

        <v-flex v-if="node.type === 0" >
            <CardTypeOne
              v-if="currentFilter === 'all' || currentFilter === 'Baskets'"
              :name="node.name"
            />
         </v-flex>

          <v-flex v-if="node.type === 1">
            <CardTypeTwo
              v-if="currentFilter === 'all' || currentFilter === 'Bots'"
              :name="node.name"
            />
          </v-flex>

        </div>
        <v-flex v-for="node in arrayData()" :key="node.num" class="flex-empty">
          <div></div>
        </v-flex>

      </v-layout>
    </v-container>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import CardTypeOne from './cardTypeOne.vue'
import CardTypeTwo from './cardTypeTwo.vue'

export default Vue.extend({
  name: 'PageList',
  components: {
    CardTypeOne,
    CardTypeTwo
  },
  data: () => ({
    currentFilter: 'all'
  }),
  methods: {
    getRandomInt (max: number) {
      return Math.floor(Math.random() * Math.floor(max))
    },
    handlerFilterBtn (data: string) {
      this.currentFilter = data
    },
    arrayData  () {
      return Array.from(new Array(10)).map((e, i) => ({
        num: i + 1,
        type: this.currentFilter === 'all'
          ? Math.floor(Math.random() * Math.floor(2))
          : this.currentFilter === 'Baskets' ? 0 : 1,
        name: `Card-${i + 1}`
      }))
    }
  }

})
</script>

<style lang="scss" scoped>
.flex {
  flex-grow: 0;
}

.flex-empty {
  height: 0 !important;
  padding-top: 0 !important;
  padding-bottom: 0 !important;

  div {
    width: 250px;
  }
}

.filter {
  button, h2 {
    margin: 10px;
  }
}
</style>
