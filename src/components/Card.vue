<template>
  <div class="card">
    <img :src="image" alt="Placeholder image" />
    <div class="container">
      <h2>{{ title }}</h2>
      <p>{{ description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: { image: String, title: String, description: String },
  components: {},
};
</script>

<style>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  border-radius: 5px;
}

img {
  border-radius: 5px 5px 0 0;
}
</style>
