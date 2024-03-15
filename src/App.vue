<template>
  <div class="top" id="app">
    <FormComp/>
  </div>
</template>

<script>
import FormComp from './components/FormComp.vue';

export default {
  name: 'App',
  components: {
    FormComp,
  }
}
</script>

<style lang="sass">
*
  padding: 0
  margin: 0

.top
  display: flex
  justify-content: center
  align-items: center

.center
  padding-left: calc(50% - 1200px / 2)
  padding-right: calc(50% - 1200px / 2)
</style>
