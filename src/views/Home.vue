<template>
  <div class="column">
    <div class="columns">
      <router-view />
      <div class="card" v-for="item in list" v-bind:key="item.id">
        <router-link to="/add">
          <img v-bind:src="item.image" alt="Placeholder image" />
        </router-link>
        <div class="container">
          <h2>{{ item.title }}</h2>
          <p>{{ item.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
      list: undefined,
    };
  },
  beforeMount() {
    axios.get('http://localhost:3000/recipes').then((res) => {
      this.list = res.data;
      console.log(res.data);
    });
  },
};
</script>
<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  border-radius: 5px;
}

img {
  width: 25rem;
  border-radius: 5px 5px 0 0;
}
.column {
  background: #f1f2f2;
  height: calc(100vh - 12vh - 2px);
}
</style>
