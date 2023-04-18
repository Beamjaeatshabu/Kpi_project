<template>
  <div class="slideshow">
    <transition-group tag="div" class="image-wrapper" :css="false" name="fade">
      <div v-for="(image, index) in images" :key="index" v-if="currentIndex === index">
        <a :href="image.link" target="_blank">
          <img :src="image.src" :alt="image.title">
        </a>
        <div class="image-title">{{ image.title }}</div>
      </div>
    </transition-group>
    <div class="controls">
      <button class="prev" @click="prevImage">&#10094;</button>
      <button class="next" @click="nextImage">&#10095;</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Slideshow',
  data() {
    return {
      currentIndex: 0,
      images: [
        {
          src:
            'https://c4.wallpaperflare.com/wallpaper/97/833/155/mountains-firewatch-green-forest-wallpaper-preview.jpg',
          title: 'Image 1',
          link: 'https://unsplash.com/photos/4k-elnPHtEY',
        },
      ],
    };
  },
  computed: {
    currentImage() {
      return this.images[this.currentIndex];
    },
  },
  methods: {
    prevImage() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      } else {
        this.currentIndex = this.images.length - 1;
      }
    },
    nextImage() {
      if (this.currentIndex < this.images.length - 1) {
        this.currentIndex++;
      } else {
        this.currentIndex = 0;
      }
    },
  },
};
</script>

<style>
.slideshow {
  position: relative;
  width: 100%;
  height: 0;
  padding-top: 60%;
  overflow: hidden;
}

.slideshow .image-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.slideshow .image-wrapper > div {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: none;
}

.slideshow .image-wrapper > div:first-child {
  display: block;
}

.slideshow .image-wrapper img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.image-title {
  position: absolute;
  bottom: 0;
  left: 0;
  color: #fff;
  font-size: 18px;
  font-weight: bold;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 10px;
  width: 100%;
  box-sizing: border-box;
}
</style>
