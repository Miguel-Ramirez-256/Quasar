<template>
  <q-page class="flex flex-center text-white">
    <div class="row">
      <q-input
      v-model="data.name"
       input-class="text-center text-h5 text-white"
       color="orange"
       placeholder="Counter"
       filled 
        />
    </div>
    <div class="row full-width items-center">
    <div class="col text-center">
      <q-btn
      @click="decreaseCouter"
      v-touch-repeat:300:300:300:300:50.mouse="decreaseCouter"
       icon="remove_circle_outline"
       size="xl"
       round 
       />
    </div>
    <div class="col text-center text-h2">
       {{ data.counter }}
      </div>
    <div class="col text-center">
      <q-btn
      @click="increaseCouter"
      v-touch-repeat:300:300:300:300:50.mouse="increaseCouter"
      icon="add_circle_outline"
      size="xl"
      round 
       />
    </div>
  </div>
  <div class="row">
    <q-btn
    @click="resetCouter"
       icon="restart_alt"
       size="xl"
       round 
       />
  </div>
  </q-page>
</template>

<style scoped>
.q-page {
  max-width: 700px;
  margin: 0 auto;
}
</style>

<script setup>

// Imports
import { reactive } from 'vue';

// Data
const data = reactive({
  counter: 0,
  name: ''
})

// Counter methods
const increaseCouter = () => {
  data.counter++
}

const decreaseCouter = () => {
  if (data.counter > 0) data.counter--
}

const resetCouter = () => {
  data.counter = 0
}
</script>
