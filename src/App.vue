<template>
  <div id="app">
    <PhotoGallery images="
      https://placeimg.com/1600/900/arch,
      https://placeimg.com/1600/900/tech,
      https://placeimg.com/1600/900/people,
      https://placeimg.com/1600/900/animals,
      https://placeimg.com/1600/900/nature,
      https://placeimg.com/1600/901/arch,
      https://placeimg.com/1600/901/tech,
      https://placeimg.com/1600/901/people,
      https://placeimg.com/1600/901/animals,
      https://placeimg.com/1600/901/nature
    "/>
  </div>
</template>

<script>
import PhotoGallery from './components/PhotoGallery.vue'

export default {
  name: 'app',
  components: {
    PhotoGallery
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: black;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
#app {
  width: 100%;
  height: 100%;
  max-width: 768px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
}
</style>
