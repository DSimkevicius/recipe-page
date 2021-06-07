<template>
  <div class="column">
    <div class="columns ">
      <router-view />
      <div class="flexbox">
        <div class="card" v-for="item in list" v-bind:key="item.id">
          <img v-bind:src="item.image" alt="Placeholder image" />
          <div class="container">
            <h2>{{ item.title }}</h2>
            <p>{{ item.description }}</p>
          </div>
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
  border-radius: 5px;
  padding: 1rem;
  margin: 1rem;
}

img {
  width: 25rem;
  border-radius: 5px 5px 0 0;
}
.column {
  background: #f1f2f2;
}

.flexbox {
  display: flex;
  flex-wrap: wrap;
  width: 50%;
  margin: 0 auto;
  justify-content: center;
  padding: 1rem;
}
.columns {
  align-items: center;
}

.wrapper {
  margin: 0 auto;
  max-width: 768px;
}
</style>
