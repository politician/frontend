<template>
  <q-page class="flex flex-center">
    <Hello name="romain" />
    <q-circular-progress
      indeterminate
      size="75px"
      :thickness="0.6"
      color="lime"
      center-color="grey-8"
      class="q-ma-md"
    />
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  components: {
    Hello: () => import('components/Hello.vue')
  }
}
</script>
