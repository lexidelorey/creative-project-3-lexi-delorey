<template>
<div>
  <div class="header">
    <h1>Search Images</h1>
  </div>
  <div class="wrapper">
    <div class="search">
      <form>
        <input v-model="searchText"/>
      </form>
    </div>
    <div class="menu">
      <ul class="menu-list">
        <li class="menu-item"><a @click="select('WA')" href="#" class="menu-link">Washington</a></li>
        <li class="menu-item"><a @click="select('FL')" href="#" class="menu-link">Florida</a></li>
        <li class="menu-item"><a @click="select('WY')" href="#" class="menu-link">Wyoming</a></li>
        <li class="menu-item"><a @click="select('UT')" href="#" class="menu-link">Utah</a></li>
        <li class="menu-item"><a @click="select('')" href="#" class="menu-link">Reset Filters</a></li>
      </ul>
    </div>
  </div>
  <ImageList :images="images" />
</div>
</template>

<script>
import ImageList from "../components/ImageList.vue"
export default {
  name: 'SearchView',
  components: {
    ImageList
  },
  data() {
    return {
      searchText: '',
      state: '',
    }
  },
  computed: {
    images() {
      if (this.state !== '') {
        let countryFilteredImages = this.$root.$data.images.filter(image => image.location === this.state);
        if (this.searchText !== '') {
          return countryFilteredImages.filter(image => image.name.toLowerCase().search(this.searchText.toLowerCase()) >= 0);
        } else {
          return countryFilteredImages;
        }
      } else if (this.searchText !== '') {
        return this.$root.$data.images.filter(image => image.name.toLowerCase().search(this.searchText.toLowerCase()) >= 0);
      } else {
        return [];
      }
    }
  },
  methods: {
    select(state) {
      this.state = state;
    }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
}
form {
  display: table;
  width: 99.3%;
}
i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}
input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}
.menu {
  margin: 10px;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

li {
  float: left;
}

li a {
  display: block;
  color: black;
  text-align: center;
  padding: 16px;
  text-decoration: none;
}
</style>
