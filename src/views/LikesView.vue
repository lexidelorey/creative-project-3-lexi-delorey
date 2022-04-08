<template>
  <div class="likes">
    <h1>Liked Images</h1>
    <ImageList :images="images" />
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
