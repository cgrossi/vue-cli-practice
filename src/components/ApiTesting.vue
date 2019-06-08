<template>
  <div id="api-test">
    <h2>Api Practicing</h2>
    <p>Dummy data is grabbed from jsonplaceholder api with axios and displayed at the 'created lifecycle hook.</p>
    <p>There is also an input box where you can filter the items by search text.</p>
    <p>
      <strong>Enter text into box below to filter images</strong>
    </p>
    <input type="text" v-model="filtered">
    <ul>
      <li v-for="photo in filterImages" :key="photo.id">
        <h4>{{ photo.title }}</h4>
        <img :src="photo.thumbnailUrl" alt="thumbnail">
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      photos: [],
      filtered: ""
    };
  },
  methods: {},
  computed: {
    filterImages() {
      return this.photos.filter(el => el.title.match(this.filtered));
    }
  },
  created: function() {
    axios.get("https://jsonplaceholder.typicode.com/photos/").then(response => {
      this.photos = response.data.filter(el => el.id < 51);
    });
  }
};
</script>

<style scoped>
#api-test {
  background-color: rgb(193, 215, 255);
}

ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  width: 600px;
  margin: 0 auto;
  padding: 10px 0;
  flex-wrap: wrap;
  justify-content: space-evenly;
  align-items: flex-start;
}

li {
  width: 200px;
  margin: 10px;
  padding: 15px 25px;
  min-height: 50px;
  background-color: rgba(250, 250, 250, 0.925);
  border: 1px solid cornflowerblue;
  border-radius: 2px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  flex-basis: auto;
}

.rule {
  border-top: 1px solid rgba(214, 214, 214, 0.904);
  padding-top: 9px;
}

p {
  margin-bottom: 8px;
}

input {
  padding: 10px 5px;
  font-size: 1.1rem;
}
</style>