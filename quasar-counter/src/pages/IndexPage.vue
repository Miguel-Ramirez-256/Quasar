<template>
  <q-page class="flex flex-center text-white">
    <div class="row">
      <q-input
       input-class="text-center text-h5 text-white"
       color="teal"
       placeholder="Counter"
       filled 
        />
    </div>
    <div class="row full-width items-center">
    <div class="col text-center">
      <q-btn
       icon="remove_circle_outline"
       size="xl"
       round 
       />
    </div>
    <div class="col text-center text-h2">23</div>
    <div class="col text-center">
      <q-btn
       icon="add_circle_outline"
       size="xl"
       round 
       />
    </div>
  </div>
  <div class="row">
    <q-btn
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

</script>
