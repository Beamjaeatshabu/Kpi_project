<template>
  <div class="slider">
    <ul>
      <li v-for="(image, index) in images" :key="index">
        <img :src="image.url" alt="">
      </li>
    </ul>
    <div class="slider-controls">
      <button @click="prevImage">Previous</button>
      <button @click="nextImage">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        { url: 'https://cdn.pixabay.com/photo/2018/01/14/23/12/nature-3082832__340.jpg' },
        { url: 'https://example.com/image2.jpg' },
        { url: 'https://example.com/image3.jpg' },
        { url: 'https://example.com/image4.jpg' },
      ],
      currentImageIndex: 0,
    };
  },
  methods: {
    prevImage() {
      this.currentImageIndex = this.currentImageIndex > 0 ? this.currentImageIndex - 1 : this.images.length - 1;
    },
    nextImage() {
      this.currentImageIndex = this.currentImageIndex < this.images.length - 1 ? this.currentImageIndex + 1 : 0;
    },
  },
  computed: {
    currentImage() {
      return this.images[this.currentImageIndex];
    }
  },
};
</script>


<style scoped>
.slider {
  position: relative;
}
.slider ul {
  list-style: none;
  margin: 0;
  padding: 0;
  position: relative;
  width: 100%;
  height: 500px;
  overflow: hidden;
}
.slider li {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}
.slider li img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.slider li:nth-child({{ currentImageIndex + 1 }}) {
  opacity: 1;
}
.slider-controls {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}
</style>
