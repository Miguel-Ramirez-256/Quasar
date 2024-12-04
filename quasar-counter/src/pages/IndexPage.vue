<template>
  <q-page 
  v-touch-pan.vertical.prevent.mouse="handlePan"
  class="flex flex-center text-white">
    <div class="row">
      <q-input
      v-model="data.name"
       input-class="text-center text-h5 text-white"
       color="orange"
       placeholder="Counter"
       filled 
        />
    </div>
    <!--Modificacion nuevo campo para elegir el incremento/decremento-->
    <div class="row"> 
      <q-input
        v-model="data.incrementValue"
        type="number"
        input-class="text-center text-h5 text-white"
        color="orange"
        placeholder="Elije el valor"
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
import { reactive, watch } from 'vue';
import { useQuasar } from 'quasar'

// Quasar
const $q = useQuasar()

// Data
const data = reactive({
  counter: 0,
  name: '',
  incrementValue: 1 // Nuevo: valor del incremento (por defecto 1)
})

const savedData = $q.localStorage.getItem('data')
if (savedData) Object.assign(data, savedData)

watch(data, value => {
  $q.localStorage.set( 'data', value )
})

// Counter methods
const increaseCouter = () => {
  const increment = parseInt(data.incrementValue) // Usar el valor del input o 1 como predeterminado
  data.counter+= increment
}

const decreaseCouter = () => {
  const decrement = parseInt(data.incrementValue) // Usar el valor del input o 1 como predeterminado
  if (data.counter > 0) 
  data.counter-= decrement
}

const resetCouter = () => {
  data.counter = 0
}

//touch pan
const handlePan = e => {
  console.log(e.delta.y)
  if (e.delta.y < 0) increaseCouter()
  else decreaseCouter()
}

</script>
