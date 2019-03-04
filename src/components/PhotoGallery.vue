<template>
  <div class="gallery">
    <div class="current" :style="{ backgroundImage: 'url('+imagesArray[currentImageIndex]+')' }">
      <div class="controls">
        <span @click="prev"><</span>
        <span @click="next">></span>
      </div>
    </div>
    
    <div class="thumbnails">
      <div class="thumbnails-container" :style="{ width: imagesArray.length * 12.5 +'%' , transform: 'translateX('+thumbnailPos+'%)' }">
        <div class="thumbnail"
          v-for="(image, index) in imagesArray" 
          :key="index"
          :style="{backgroundImage: 'url(' + image + ')'}"
          :class="{ active: currentImageIndex == index ? true : false  }"
          @click="changeCurrent(index)"
          >
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'PhotoGallery',
  props: {
    images: String
  },
  data() {
    return {
      thumbnailPos : 0,
      currentImageIndex: 0,
    }
  },
  methods: {
    prev : function(){
      this.thumbnailPos = this.thumbnailPos + 100 / this.imagesArray.length
      if(this.thumbnailPos >= 0){
        this.thumbnailPos = 0
      }
      this.currentImageIndex > 0 ? this.currentImageIndex-- : this.currentImageIndex
    },
    next : function(){
      this.thumbnailPos = this.thumbnailPos - 100 / this.imagesArray.length
      if(this.thumbnailPos <= -100 / this.imagesArray.length * (this.imagesArray.length - 8) ){
        this.thumbnailPos = -100 / this.imagesArray.length * (this.imagesArray.length - 8)
      }
      this.currentImageIndex == this.imagesArray.length-1 ? this.currentImageIndex : this.currentImageIndex++
    },
    changeCurrent: function(index){
      this.currentImageIndex = index;
    }
  },
  computed: {
    imagesArray: function(){
      return this.images.split(",")
    },
  },
  mounted() {
  },
}
</script>

<style scoped>
.gallery {
  width: 100%;
  min-width: 320px;
  background-color: grey;
  padding: 0 1rem;
}
.current {
  margin: 1rem 0;
  display: flex;
  justify-content: center;
  min-height: 400px;
  max-height: 600px;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  transition: all 0.3s;
  position: relative;
}
.thumbnails {
  margin: 1rem 0;
  width: 100%;
  overflow: hidden;
  position: relative;
  height: 90px;
  cursor: pointer;
}
.thumbnails-container {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: row;
  transition: all 0.3s;

}
.thumbnail {
  width: 12.5%;
  height: 90px;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  border: 1px solid black;
  background-color: black;
  opacity: 0.3;
}
.thumbnail.active {
  opacity: 1
}
.controls {
  position: absolute;
  top: 50%;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%)
}
.controls > span {
  color: black;
  background-color: white;
  font-weight: bold;
  width: 40px;
  height: 40px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-transform: uppercase;
  cursor: pointer;
  user-select: none;
}
</style>
