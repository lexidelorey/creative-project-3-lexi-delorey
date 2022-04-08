<template>
  <div class="home">
    <div class="header">
      <h1>Image Feed</h1>
    </div>
    <ImageList :images="images" />
    <footer>
        Photos all taken by me :). Code for this website can be found on my <a href="https://github.com/lexidelorey/creative-project-3-lexi-delorey">Github</a>
    </footer>
  </div>
</template>

<script>
import ImageList from '../components/ImageList.vue'

export default {
  name: 'HomeView',
  components: {
    ImageList
  },
  computed: {
    images() {
      return this.$root.$data.images;
    }
  }
}
</script>

<style scoped>
footer {
  box-sizing: border-box;
  text-align: center;
  width: 100%;
  margin-top: 20px;
  padding: 50px;
  background-color: #416788;
  color: white;
  font-size: 1em;
  position: absolute;
}
</style>
