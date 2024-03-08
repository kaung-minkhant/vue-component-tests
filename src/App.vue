<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <SuggestionBox :search-list="devices" search-key="name" select-field="name" @selected="selected"/>
</template>

<script>
import SuggestionBox from './components/SuggestionBox/SuggestionBox.vue';

export default {
  name: 'App',
  data() {
    return {
      devices: [
        {
          name: 'LED'
        },
        {
          name: 'TV'
        },
        {
          name: 'Refrigerator'
        },
      ]
    }
  },
  methods: {
    selected(device) {
      console.log(device)
    }
  },
  components: {
    SuggestionBox
  }
}
</script>

<style>
</style>
