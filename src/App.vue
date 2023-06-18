<template>
  <ul>
      <learning-resource v-for="res in storedResources" 
      :key="res.id"
      :name="res.name"
      :description="res.description"
      :link="res.link"
      ></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './components/learning-resources/LearningResource.vue';
export default {
  components: {
      LearningResource
  },
  data() {
      return {
          storedResources: [
              {
                  id: 1,
                  name: 'Resource 1',
                  description: 'Vue documentation',
                  link: 'https://www.vuejs.org'
              },
              {
                  id: 2,
                  name: 'Resource 2',
                  description: 'This is the description for google',
                  link: 'https://www.google.com'
              },
              {
                  id: 3,
                  name: 'Resource 3',
                  description: 'This is the description for resource 3',
                  link: 'https://www.google.com'
              }

          ]
      }
  },
  methods: {
     
  },

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
box-sizing: border-box;
}

html {
font-family: 'Roboto', sans-serif;
}

body {
margin: 0;
}

</style>
