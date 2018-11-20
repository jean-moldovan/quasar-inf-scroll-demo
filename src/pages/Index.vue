<template>
  <q-page>
    <div class="text-center q-py-sm">
      <q-btn size="lg" label="Stop This!" color="primary" @click="$refs.inf.stop()" class="q-mr-sm">
      </q-btn>

      <q-btn size="lg" label="Destroy This!" color="primary" @click="show = false">
      </q-btn>
    </div>

    <q-infinite-scroll v-if="show" :handler="load" ref="inf">
      <div v-for="item in items" :key="item" class="item">
        {{ item }}
      </div>
    </q-infinite-scroll>

    <div v-else style="minHeight: 5000px" class="q-pa-md">
      Container with scroll for testing purposes
    </div>

  </q-page>
</template>

<style>
.item {
  font-size: 32px;
  font-weight: bold;
  border: 2px solid orange;
  padding: 32px;
  min-height: 200px;
}
</style>

<script>
import { QInfiniteScroll } from 'quasar'

export default {
  name: 'PageIndex',
  components: {
    QInfiniteScroll
  },
  data () {
    return {
      show: true,
      items: []
    }
  },
  methods: {
    load (i, done) {
      setTimeout(() => {
        this.items.push(i)
        done()
      }, 1000)
    }
  }
}
</script>
