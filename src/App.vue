<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <SuggestionBox :search-list="devices" search-key="name" select-field="name" @selected="selected" :max-suggestion="4" />
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
          name: 'Laptop'
        },
        {
          name: 'TV'
        },
        {
          name: 'Refrigerator'
        },
        {
          name: 'Fan'
        },
        {
          name: 'Pump'
        },
        {
          name: 'Microwave'
        },
        {
          name: 'Washing Machine'
        },
        {
          name: 'CCTV'
        },
        {
          name: 'AC'
        },
        {
          name: 'Computer'
        },
        {
          name: 'Tablet'
        },
        {
          name: 'Mobile'
        },
        {
          name: 'Speaker'
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
