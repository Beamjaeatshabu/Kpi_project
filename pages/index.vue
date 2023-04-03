<template>
  <div>
    <div class="slideshow">
      <transition-group tag="div" class="image-wrapper" :css="false" name="fade">
        <div v-for="(image, index) in images" :key="index" v-if="currentIndex === index">
          <a :href="image.link" target="_blank">
            <img :src="image.src" :alt="image.title">
          </a>
        </div>
      </transition-group>
    </div>
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
            'https://www.lppproperty.co.th/wp-content/uploads/2022/12/Photo-Banner-3.jpg',
          title: 'Image 1',
          link: 'https://unsplash.com/photos/4k-elnPHtEY',
        },
        {
          src:
            'https://www.lppproperty.co.th/wp-content/uploads/2022/12/Photo-Banner-2-2.jpg',
          link: 'https://unsplash.com/photos/4k-elnPHtEY',
        },
        {
          src:
            'https://www.lppproperty.co.th/wp-content/uploads/2022/12/Photo-Banner-1-2.jpg',
          title: 'Image 3',
          link: 'https://unsplash.com/photos/4k-elnPHtEY',
        },
        {
          src:
            'https://www.lppproperty.co.th/wp-content/uploads/2022/12/Photo-Banner-4-1.jpg',
          title: 'Image 4',
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

.controls {
  margin-top: 10px;
  text-align: center;
}

.controls button {
  background-color: #f2f2f2;
  border: none;
  color: black;
  padding: 10px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}

.controls button:hover {
  background-color: #ddd;
}

.prev {
  float: left;
}

.next {
  float: right;
}
</style>
