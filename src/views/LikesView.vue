<template>
  <div class="likes">
    <h1>Liked Images</h1>
    <ImageList :images="images" />
    <footer>
        Photos all taken by me :). Code for this website can be found on my <a href="https://github.com/lexidelorey/creative-project-3-lexi-delorey">Github</a>
    </footer>
  </div>
</template>

<script>
import ImageList from '../components/ImageList.vue'

export default {
  name: 'LikesView',
  components: {
    ImageList
  },
  computed: {
    images() {
      return this.$root.$data.images.filter(image => image.like == true);
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
